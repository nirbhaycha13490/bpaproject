<script>
    import { fly } from 'svelte/transition';
    import { Rocket, GraduationCap, Swords } from 'lucide-svelte';


    const features = [
        {
            icon: GraduationCap,
            title: 'Lectures',
            description: 'We teach to our members engineering concepts and disciplines from numerous fields.',
            delay: 100
        },
        {
            icon: Swords,
            title: 'Competitions',
            description: 'We host engineering competitions that can earn our members scholarships and medals.',
            delay: 1000
        },
        {
            icon: Rocket,
            title: 'Projects',
            description: 'We host interactive projects to expose members to real-world engineering scenarios.',
            delay: 300
        }
    ];
</script>



<div class="container">
    <section class="hero">
        <div class="hero-content" in:fly={{ y: 20, duration: 600 }}>
            <h1>
                <span class="text-accent">Engineering</span>
                <span class="text-gradient">for the community</span>
            </h1>
            <p class="hero-text">Join us on our mission to shape the future of engineering and innovation.</p>
            <div class="cta-buttons">
                <a href="/meetings" class="button primary">Join Us</a>
                <a href="/about" class="button secondary">Learn More</a>
            </div>
        </div>
    </section>

    <section class="features">
        <h2 in:fly={{ y: 20, duration: 600 }}>What We Do</h2>
        <div class="features-grid" in:fly={{ y: 20, duration: 600, delay: 100 }}>
            {#each features as feature}
                <div class="feature-card glass">
                    <div class="feature-icon">
                        <svelte:component this={feature.icon} size={32} />
                    </div>
                    <h3>{feature.title}</h3>
                    <p>{feature.description}</p>
                </div>
            {/each}
        </div>
    </section>
	<!--
    <section class="projects">
        <h2>Latest Projects</h2>
        <div class="projects-grid">
            <div class="project-card glass" in:fly={{ y: 20, duration: 600 }}>
                <img src="/projects/placeholder.jpg" alt="blank one" />
                <div class="content">
                    <h3>blank one</h3>
                    <p>blank one</p>
                </div>
            </div>
            <div class="project-card glass" in:fly={{ y: 20, duration: 600, delay: 200 }}>
                <img src="/projects/placeholder.jpg" alt="blank two" />
                <div class="content">
                    <h3>blank two</h3>
                    <p>blank two</p>
                </div>
            </div>
            <div class="project-card glass" in:fly={{ y: 20, duration: 600, delay: 400 }}>
                <img src="/projects/placeholder.jpg" alt="Website Development" />
                <div class="content">
                    <h3>blank three</h3>
                    <p>blank three</p>
                </div>
            </div>
        </div>
    </section>
	-->

    <section class="join">
        <div class="join-content glass" in:fly={{ y: 20, duration: 600 }}>
            <h2>Ready to Join?</h2>
            <p>Be part of something amazing. Join us in our next meeting and start your engineering journey.</p>
            <div class="join-details">
                <div class="detail">
                    <h4>When</h4>
                    <p>Every Other Friday @ Advisory</p>
                </div>
                <div class="detail">
                    <h4>Where</h4>
                    <p>Room B213</p>
                </div>
            </div>
            <a href="/meetings" class="button primary">View Schedule</a>
        </div>
    </section>
</div>

<style>
    .hero {
        padding: var(--space-16) 0;
        text-align: center;
    }

    .hero-content {
        max-width: 800px;
        margin: 0 auto;
    }

    h1 {
        font-size: clamp(2.5rem, 8vw, 4rem);
        line-height: 1.1;
        margin-bottom: var(--space-6);
    }

    .text-accent {
        display: block;
        color: var(--text-primary);
    }

    .hero-text {
        font-size: var(--text-xl);
        color: var(--text-secondary);
        margin-bottom: var(--space-8);
        max-width: 600px;
        margin-left: auto;
        margin-right: auto;
    }

    .cta-buttons {
        display: flex;
        gap: var(--space-4);
        justify-content: center;
    }

    .button {
        padding: var(--space-3) var(--space-6);
        border-radius: var(--border-radius-lg);
        text-decoration: none;
        font-weight: 500;
        transition: all var(--transition);
    }

    .button.primary {
        background: var(--primary);
        color: var(--surface-0);
    }

    .button.primary:hover {
        transform: translateY(-2px);
        box-shadow: 0 4px 12px var(--primary-hover);
    }

    .button.secondary {
        background: var(--surface-100);
        color: var(--text-primary);
    }

    .button.secondary:hover {
        background: var(--surface-200);
        transform: translateY(-2px);
    }

    .features {
        padding: var(--space-16) 0;
    }

    h2 {
        text-align: center;
        margin-bottom: var(--space-12);
        font-size: var(--text-3xl);
    }

    .features-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        gap: var(--space-6);
    }

    .feature-card {
        padding: var(--space-6);
        border-radius: var(--border-radius-2xl);
        text-align: center;
        transition: transform var(--transition);
    }

    .feature-card:hover {
        transform: translateY(-4px);
    }

    .feature-icon {
        width: 64px;
        height: 64px;
        margin: 0 auto var(--space-4);
        display: flex;
        align-items: center;
        justify-content: center;
        border-radius: 50%;
        background: var(--surface-100);
        color: var(--primary);
    }

    .feature-card h3 {
        margin: 0 0 var(--space-2);
        font-size: var(--text-xl);
    }

    .feature-card p {
        color: var(--text-secondary);
        line-height: 1.6;
    }

    .projects {
        padding: var(--space-16) 0;
    }

    .projects-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: var(--space-6);
    }

    .project-card {
        border-radius: var(--border-radius-2xl);
        overflow: hidden;
        transition: transform var(--transition);
    }

    .project-card:hover {
        transform: translateY(-4px);
    }

    .project-image {
        width: 100%;
        height: 200px;
        overflow: hidden;
    }

    .project-image img {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

    .project-content {
        padding: var(--space-6);
    }

    .project-content h3 {
        margin: 0 0 var(--space-2);
        font-size: var(--text-xl);
    }

    .project-content p {
        color: var(--text-secondary);
        margin: 0;
        line-height: 1.6;
    }

    .join {
        padding: var(--space-16) 0;
    }

    .join-content {
        max-width: 600px;
        margin: 0 auto;
        text-align: center;
        padding: var(--space-8);
        border-radius: var(--border-radius-2xl);
    }

    .join-content h2 {
        margin-bottom: var(--space-4);
    }

    .join-content p {
        color: var(--text-secondary);
        margin-bottom: var(--space-8);
    }

    .join-details {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: var(--space-6);
        margin-bottom: var(--space-8);
    }

    .detail h4 {
        color: var(--primary);
        margin: 0 0 var(--space-2);
        font-size: var(--text-lg);
    }

    .detail p {
        margin: 0;
    }

    .test-image {
        width: 300px;
        height: 300px;
        margin: 20px;
    }
    .test-image img {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

    @media (max-width: 768px) {
        .hero {
            padding: var(--space-8) 0;
        }

        .features, .projects, .join {
            padding: var(--space-8) 0;
        }

        h2 {
            margin-bottom: var(--space-8);
        }

        .join-details {
            grid-template-columns: 1fr;
            gap: var(--space-4);
        }
    }
</style>