<script lang="ts">
	import Slide from "$lib/components/Slide.svelte";
    import { fly } from "svelte/transition";
</script>

<div class="container">
    <section class="hero" in:fly={{ y: 20, duration: 600 }}>
        <h2>Next Meeting</h2>
        <div class="meeting-info">
            <h1 style="color: var(--primary);">January 1, 2025</h1>
            <h3>Mr. Patton's room</h3>
            <h3>B213 @ Advisory</h3>
        </div>
    </section>

    <section class="slides">
        <h2 in:fly={{ y: 20, duration: 600, delay: 100 }}>Past Meeting Slides</h2>
        <div class="slides-grid grid">
            <Slide
                src="10-10-2024" 
                date="October 10, 2024"
                delay={200}
            />
            <Slide 
                src="11-14-2024" 
                date="November 14, 2024"
                delay={300}
            />
        </div>
    </section>
</div>

<style>
    .hero {
        text-align: center;
        padding: var(--space-16) 0 0 0;
    }

    .hero h1 {
        margin-bottom: var(--space-4);
    }

    .hero p {
        color: var(--text-secondary);
        font-size: var(--text-xl);
        max-width: 600px;
        margin: 0 auto;
    }

    .meeting-info {
        display: flex;
        flex-direction: column;
        gap: var(--space-2);
    }

    .meeting-info h2 {
        line-height: 1;
        color: var(--text-primary);
    }

    .slides {
        padding: var(--space-16) 0;
    }

    .slides h2 {
        text-align: center;
        margin-bottom: var(--space-8);
        font-size: var(--text-3xl);
    }

    .slides-grid {
        display: grid;
        grid-template-columns: 1fr;
        gap: var(--space-8);
        max-width: 1200px;
        margin: 0 auto;
    }

    .slides-container {
        width: 100%;
        height: 600px;
        position: relative;
        overflow: hidden;
        border-radius: var(--border-radius-lg);
        margin-bottom: var(--space-4);
    }

    .slides-container iframe {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        border: none;
    }

    .card {
        padding: var(--space-6);
        margin-bottom: var(--space-6);
        border-radius: var(--border-radius-xl);
    }

    .grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
        gap: var(--space-6);
        margin-bottom: var(--space-8);
    }

    @media (max-width: 768px) {
        .hero {
            padding: var(--space-8) 0;
        }

        .slides {
            padding: var(--space-8) 0;
        }

        .slides-container {
            height: 400px;
        }
    }
</style>