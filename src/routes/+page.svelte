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
            delay: 200
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
                <span class="text-accent">Rock </span>
                <span class="text-gradient">for the Masses</span>
            </h1>
            <p class="hero-text">"With Stage Fright, the lights shine brighter, the beats hit harder, and the crowd roars louder."
            </p>
            <div class="cta-buttons">
                <a href="/about" class="button primary">Learn More</a>
                <a href="/contact" class="button secondary">Contact Us</a>

            </div>
        </div>
    </section>
    <center><h2> Welcome</h2></center>
    <center><p>Hello, and welcome to Stage Fright, the hottest up-and-coming rock band! Stage Fright is an exciting new powerhouse of modern rock, combining electrifying guitar riffs, powerful vocals, and unique percussion to build songs unlike anything else. Every performance by Stage Fright isn’t just a concert; it’s a complete experience. With great music, charismatic band members, and a connection with the crowd, Stage Fright sets itself apart from its competitors to create a unique escapade that will leave a lasting impact. So, turn up the volume, feel the energy, and join the movement—because the music doesn’t just play with Stage Fright. It hits.
        </p></center>


    <section class="join">
        <div class="join-content glass" in:fly={{ y: 20, duration: 600 }}>
            <h2>Feel the Rhythm, Join the Movement            </h2>
            <p>Experience the energy, passion, and unforgettable performances of Stage Fright – join us and be part of the movement that's redefining rock music for the masses.            </p>
            <div class="join-details">
                <div class="detail">
                    <h4>Next Concert</h4>
                    <p>January 20, 2025                    </p>
                </div>
                <div class="detail">
                    <h4>Where</h4>
                    <p>Madison Square Garden, NY                    </p>
                </div>
            </div>
            <a href="/meetings" class="button primary">View Tour Dates</a>
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



    h2 {
        text-align: center;
        margin-bottom: var(--space-12);
        font-size: var(--text-3xl);
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


    @media (max-width: 768px) {
        .hero {
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