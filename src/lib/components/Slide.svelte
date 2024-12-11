<script lang="ts">
    import { fly } from "svelte/transition";
    import * as pdfjs from "pdfjs-dist";
    import { onMount } from "svelte";
    import { ChevronLeft, ChevronRight } from 'lucide-svelte';
    import type { RenderParameters } from "pdfjs-dist/types/src/display/api";
    pdfjs.GlobalWorkerOptions.workerSrc = new URL("pdfjs-dist/build/pdf.worker.mjs", import.meta.url).toString();
    console.log(import.meta.url);
    let canvas: HTMLCanvasElement;
    let viewport: pdfjs.PageViewport;
    let context: CanvasRenderingContext2D | null;
    let pdf: pdfjs.PDFDocumentProxy;
    let renderContext: RenderParameters;
    let currentPage = 1;

    onMount(async () => {
        const loadingTask = pdfjs.getDocument(`meetings/${src}.pdf`);
        pdf = await loadingTask.promise;
        const page = await pdf.getPage(currentPage);
        viewport = page.getViewport({ scale: 1 });
        context = canvas.getContext("2d");
        canvas.height = viewport.height;
        canvas.width = viewport.width;

        if (!context) return;

        renderContext = {
            canvasContext: context,
            viewport: viewport,
        };

        await page.render(renderContext);
    });

    async function changePage(next: number) {
        if (currentPage + next < 1 || currentPage + next > pdf.numPages) return;
        currentPage += next;
        const page = await pdf.getPage(currentPage);

        if (!context) return;
        await page.render(renderContext);
    }

    export let src: string;
    export let date: string;
    export let delay: number;
</script>

<div class="slide-card glass" in:fly={{ y: 20, duration: 600, delay: delay }}>
    <div class="slides-container">
        <!--<object
            data="/meetings/{src}.pdf"
            type="application/pdf"
            width="100%"
            height="800"
        >
            <p>Unable to display PDF. <a href="/meetings/{src}.pdf" target="_blank">Download Instead</a></p>
        </object>-->
        {#if !pdf}<h3 class="fail">PDF failed to load.</h3>{/if}
        <canvas bind:this={canvas}></canvas>
    </div>
    <div class="content">
        <div>
            <div class="date">{date}</div>
            <a href="meetings/{src}.pdf" target="_blank" class="view-button">View Full Screen</a>
        </div>
        <div class="slide-buttons">
            <button onclick={async () => { changePage(-1) }} disabled={!pdf || currentPage <= 1}>
                <div class="feature-icon">
                    <ChevronLeft size={32} />
                </div>
            </button>
            <button onclick={async () => { changePage(1) }} disabled={!pdf || currentPage >= pdf.numPages}>
                <div class="feature-icon">
                    <ChevronRight size={32} />
                </div>
            </button>
        </div>
    </div>
</div>

<style>
    .slide-card {
        display: flex;
        flex-direction: column;
        overflow: hidden;
        border-radius: var(--border-radius-xl);
        transition: transform var(--transition);
        background: rgba(18, 18, 18, 0.7);
    }

    canvas {
        width: 100%;
        color: white;
    }

    .fail {
        position: absolute;
        width: 100%;
        margin: var(--space-6);
    }

    .slides-container {
        width: 100%;
    }

    .content {
        padding: var(--space-6);
        display: flex;
        justify-content: space-between;
    }

    .slide-buttons > button {
        width: 64px;
        height: 64px;
        padding: 0;
        border-radius: 50%;
        background: var(--surface-200);
        border: none;
        transition: all var(--transition);
        color: var(--text-primary);
        margin-left: var(--space-2);
    }

    .slide-buttons > button:not(:disabled):hover {
        background: var(--primary);
        color: var(--surface-0);
        transform: translateY(-2px);
        box-shadow: 0 4px 12px var(--primary-hover);
    }

    .slide-buttons > button:disabled {
        background: var(--surface-100);
    }

    .feature-icon {
        width: 100%;
        height: 100%;
        margin: 0 auto var(--space-4);
        display: flex;
        align-items: center;
        justify-content: center;
        color: inherit;
    }

    .date {
        color: var(--primary);
        font-size: var(--text-sm);
        margin-bottom: var(--space-2);
    }

    h3 {
        margin: 0 0 var(--space-2);
        font-size: var(--text-xl);
    }

    p {
        margin: 0 0 var(--space-4);
        color: var(--text-secondary);
        font-size: var(--text-base);
        line-height: 1.6;
    }

    .view-button {
        display: inline-flex;
        align-items: center;
        gap: var(--space-2);
        padding: var(--space-2) var(--space-4);
        background: var(--surface-200);
        color: var(--text-primary);
        text-decoration: none;
        border-radius: var(--border-radius-lg);
        font-size: var(--text-sm);
        transition: all var(--transition);
    }

    .view-button:hover {
        background: var(--primary);
        color: var(--surface-0);
        transform: translateY(-2px);
    }

    @media (max-width: 768px) {
        
    }
</style>