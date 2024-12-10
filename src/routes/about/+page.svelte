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
        <p>The Reedy TAME Engineering Club inspires students to explore STEM through hands-on projects, innovative problem-solving, and collaboration. We foster a supportive environment where members can develop critical skills, build connections, and prepare for future careers in engineering and beyond.</p>
        <br/><h2>About TAME</h2>
        <p>TAME programs depend on the support of over 800 volunteers from local STEM industries, schools, libraries, and communities. The TAME State Office is staffed by dedicated professionals who coordinate TAME's day-to-day work, support Club Leaders and Region activities, and plan for the organization’s long-term growth.</p>
        <br/><h2>TAME's Misson</h2>
        <p>TAME creates equitable experiences for students from underrepresented groups to explore futures in engineering by fostering their sense of belonging and equipping them with knowledge, skills, and intergenerational support through statewide programming at no cost to students.</p>
    </section>
    <section class="team">
        <h2>Our Team</h2>
        <div class="team-grid">
            {#each officers as officer}
                <div class="officer-card glass" in:fly={{ y: 20, duration: 600 }}>
                    <h3>{officer.title}</h3>
                    <img src="images/hero-bg.jpg"/>
                    <p style="line-height: 0;">{officer.description}</p>
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

    .team-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
        gap: var(--space-6);
        place-content: center;
        margin-top: var(--space-6);
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
        font-size: var(--text-3xl);
    }

    h3 {
        margin: 0;
        font-size: var(--text-xl);
    }

    p {
        color: var(--text-secondary);
        font-size: var(--text-lg);
        margin-top: var(--space-4);
        line-height: 2.4;
    }

    @media (max-width: 768px) {
        .hero {
            padding: var(--space-8) 0;
        }
    }
</style>