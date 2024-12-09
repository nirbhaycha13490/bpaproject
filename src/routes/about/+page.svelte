<script>
    import { fly } from 'svelte/transition';

    const officers = [
        {
            title: 'Saksham Shukla',
            description: 'CEO of this club'
        },
        {
            title: "Aman Rai",
            description: "The Rai of Aman"
        },
        {
            title: "Brandon Thames",
            description: "Website Developer"
        },
        {
            title: "Yuvraj Bathula",
            description: "Website Developer"
        }
    ];
</script>

<div class="container">
    <section class="hero">
        <h1 class="text-gradient">About Us</h1>
        <p class="subtitle">Allow us to introduce ourselves</p>
    </section>
    <section class="team">
        <h2>Who We Are</h2>
        <div class="team-grid">
            {#each officers as officer}
                <div class="officer-card glass" in:fly={{ y: 20, duration: 600 }}>
                    <h3>{officer.title}</h3>
                    <img src="images/hero-bg.jpg"/>
                    <p>{officer.description}</p>
                </div>
            {/each}
        </div>
    </section>
</div>

<style>
    .hero {
        padding: var(--space-16) 0;
        text-align: center;
    }

    .subtitle {
        color: var(--text-secondary);
        font-size: var(--text-lg);
        margin-top: var(--space-4);
    }

    .team-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
        gap: var(--space-6);
        place-content: center;
    }

    .officer-card {
        border-radius: var(--border-radius-2xl);
        transition: transform var(--transition);
        padding: var(--space-8);
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: center;
        gap: var(--space-4);
    }

    .officer-card:hover {
        transform: translateY(-4px);
    }

    .officer-card img {
        height: 250px;
        width: 240px;
        border-radius: var(--border-radius);
        object-fit: cover;
    }

    h2 {
        text-align: center;
        margin-bottom: var(--space-12);
        font-size: var(--text-3xl);
    }

    h3 {
        margin: 0;
        font-size: var(--text-xl);
    }

    p {
        color: var(--text-secondary);
        margin: 0;
        line-height: 1.6;
    }

    @media (max-width: 768px) {
        .hero {
            padding: var(--space-8) 0;
        }
    }
</style>