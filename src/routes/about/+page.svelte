<script>
    import { fly } from 'svelte/transition';

    const officers = [
        {
            title: 'Jonathan Henry',
            description: 'Vocalist',
            img: "team/vocalist.png",
            delay: 100,
            additionalText: 'The voice that commands the band, bringing raw passion and talent to every vocalist. He spends his free time tuning the art of rock. But, he strives for perfection and settles for nothing less, causing constant artistic disputes as the band argues about perfecting the music. His hobbies include soccer, tennis, and working on his car.'
        },
        {
            title: "Doug Green",
            description: "Guitarist",
            img: "team/singer.png",
            delay: 200,
            additionalText: 'A master of solos and strings, creating the unique musical background the band prides itself upon. He’s known for being the negotiator for the band, willing to give and take to make sure the sound is as good as can be. He also is a chill guy to hang out with, preferring to watch movies and read books.'
        },
        {
            title: "Thomas Patton",
            description: "Drummer",
            img: "team/drummer.png",
            delay: 300,
            additionalText: 'The heartbeat of the band, pounding every song with passion and precision to make the ultimate beat. He often stands against Jonathan, disagreeing with his vocal-heavy songs and insisting upon the importance of drums. When he’s not making music, he loves restoring vintage drum kits, exploring nature, and experimenting with percussion.'
        }
    ];
</script>

<div class="container">
    <section class="hero">
        <div in:fly={{ y: 20, duration: 600 }}>
            <h1 class="text-gradient">About Us</h1>
            <p>Stage Fright is a high-energy rock band redefining the music scene with its raw and electrifying performances. Founded with a shared passion for music, the band is making significant waves in the industry, and its new releases are shaking up the scene. The band got its first gigs playing for local events in its humble small town but has since taken to the stars with massive success. Today, they are changing the game for the rock genre, performing at much larger venues and captivating their crowds with unforgettable experiences.
                Born from late-night jam sessions in a quaint suburban garage, Stage Fright takes its roots from a dedicated group of friends who refused to dream small. Founded in 2020 in Frisco, TX, the band was inspired by legends such as Nirvana, Led Zeppelin, and Guns N’ Roses. When it came time to choose a name, it seemed to write itself, as during their first-ever performance, they complained of stage fright before giving a performance described as the “best I’ve ever heard” by local newspaper reporter Robert Dahl. Their story is simple yet powerful, showing the sheer power that anyone has when they put their mind to something.
            </p>
        </div>
        <div in:fly={{ y: 20, duration: 600, delay: 100 }}>
            <h2>Our band members</h2>
            <p>Each member of Stage Fright brings their unique energy and talent to the band, helping form a cohesive and united sound that cannot be replicated anywhere else:</p>
        </div>
    </section>
    <section class="team">
        <div class="team-grid">
            {#each officers as officer}
                <div class="officer-card glass" in:fly|global={{ y: 20, duration: 600, delay: officer.delay }}>
                    <div class="card-inner">
                        <div class="card-front">
                            <h3>{officer.title}</h3>
                            <div class="image-container">
                                <img src={officer.img} alt="{officer.title}" />
                            </div>
                            <p>{officer.description}</p>
                        </div>
                        <div class="card-back">
                            <h3>{officer.title}</h3>
                            <p>{officer.additionalText}</p>
                        </div>
                    </div>
                </div>
            {/each}
        </div>
    </section>
</div>

<style>
.hero {
    padding: var(--space-16) 0 0 0;
    text-align: center;
}

.hero > div {
    margin-bottom: var(--space-12);
}

.team {
    margin-bottom: var(--space-36);
    position: relative;
}

.team-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: var(--space-6);
    place-content: center;
    margin-top: var(--space-6);
}

.officer-card {
    position: relative;
    z-index: 1;
    perspective: 1000px;
    min-height: 500px;
}

.card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    transform-style: preserve-3d;
    transition: transform 0.6s;
}

.officer-card:hover .card-inner {
    transform: rotateY(180deg);
}

.card-front,
.card-back {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    backface-visibility: hidden;
    border-radius: var(--border-radius-2xl);
    display: flex;
    flex-direction: column;
    justify-content: center; /* Center vertically */
    align-items: center; /* Center horizontally */
    gap: var(--space-4);
    padding: var(--space-8);
}

.card-back {
    background: var(--surface-200);
    transform: rotateY(180deg);
}

.card-front h3,
.card-back h3 {
    margin-bottom: var(--space-2);
}

.card-front p,
.card-back p {
    margin-top: -0.5rem; /* Adjust position to move higher */
}

.image-container {
    height: 360px;
    width: 280px;
    overflow: hidden;
    border-radius: var(--border-radius);
    display: flex;
    align-items: center;
    justify-content: center;
}

.image-container img {
    width: auto;
    height: 100%;
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
    line-height: 2.4;
}

@media (max-width: 768px) {
    .hero {
        padding: var(--space-8) 0;
    }

    .team {
        margin-bottom: var(--space-20);
    }
}
</style>
