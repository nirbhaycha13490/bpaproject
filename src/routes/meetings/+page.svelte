<script lang="ts">
	import Slide from "$lib/components/Slide.svelte";
</script>

<div class="container">
    <section class="hero">
        <h1>Next Meeting</h1>
        <div class="meeting-info">
            <h2>January 1, 2025</h2>
            <h2>Mr. Patton's room</h2>
            <h2>(B213) @ Adv'</h2>
        </div>
    </section>

    <section class="slides">
        <h2>Past Meeting Slides</h2>
        <div class="slides-grid grid">
            <Slide 
                src="10-10-2024" 
                date="October 10, 2024" 
            />
            <Slide 
                src="10-10-2024" 
                date="October 10, 2024" 
            />
        </div>
    </section>
</div>

<style>
    .hero {
        text-align: center;
        padding: var(--space-16) 0;
    }

    .hero h1 {
        font-size: var(--text-4xl);
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
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
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