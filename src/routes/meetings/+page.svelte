<script lang="ts">
	import Slide from "$lib/components/Slide.svelte";
    import { fly } from "svelte/transition";
</script>

<div class="container">
    <section class="hero" in:fly={{ y: 20, duration: 600 }}>
        <h2>Next Concert</h2>
        <div class="meeting-info" in:fly={{ y: 20, duration: 600, delay: 200 }}>
            <center><h1 style="color: var(--primary);">January 20, 2025</h1></center>
            <center><h3>Madison Square Garden</h3></center>
            <center><h5>New York City, New York</h5></center>
            <center>
                <img 
                    src="concert locations/madisonsquare.png" 
                    alt="Madison Square Garden" 
                    style="width: 100%; max-width: 600px; margin-top: var(--space-4); border-radius: var(--border-radius-lg);"
                />
            </center>
        </div>
    </section>

    <br>
    <center><h4 in:fly={{ y: 20, duration: 500, delay: 300 }}> | </h4></center>
    <center><h4 in:fly={{ y: 20, duration: 500, delay: 400 }}> | </h4></center>
    <center><h4 in:fly={{ y: 20, duration: 500, delay: 500 }}> | </h4></center>
    <center><h4 in:fly={{ y: 20, duration: 500, delay: 600 }}> | </h4></center>
    <center><h4 in:fly={{ y: 20, duration: 500, delay: 700 }}> | </h4></center>
    <center><h4 in:fly={{ y: 20, duration: 500, delay: 800 }}> | </h4></center>
    <center><h4 in:fly={{ y: 20, duration: 500, delay: 900 }}> V </h4></center>

    <div class="meeting-info" in:fly={{ y: 20, duration: 600, delay: 1000 }}>
        <center><h1 style="color: var(--primary);">February 10, 2025</h1></center>
        <center><h3>Red Rock Amphitheater</h3></center>
        <center><h5>Morrison, Colorado</h5></center>
        <center>
            <img 
                src="concert locations/redrock.png" 
                alt="Red Rock Amphitheater" 
                style="width: 100%; max-width: 600px; margin-top: var(--space-4); border-radius: var(--border-radius-lg);"
            />
        </center>
    </div>

    <br>
    <center><h4 in:fly={{ y: 20, duration: 500, delay: 1100 }}> | </h4></center>
    <center><h4 in:fly={{ y: 20, duration: 500, delay: 1200 }}> | </h4></center>
    <center><h4 in:fly={{ y: 20, duration: 500, delay: 1300 }}> | </h4></center>
    <center><h4 in:fly={{ y: 20, duration: 500, delay: 1400 }}> | </h4></center>
    <center><h4 in:fly={{ y: 20, duration: 500, delay: 1500 }}> | </h4></center>
    <center><h4 in:fly={{ y: 20, duration: 500, delay: 1600 }}> | </h4></center>
    <center><h4 in:fly={{ y: 20, duration: 500, delay: 1700 }}> V </h4></center>

    <div class="meeting-info" in:fly={{ y: 20, duration: 600, delay: 1800 }}>
        <center><h1 style="color: var(--primary);">March 2, 2025</h1></center>
        <center><h3>American Airlines Center</h3></center>
        <center><h5>Dallas, Texas</h5></center>
        <center>
            <img 
                src="concert locations/americanairlines.png" 
                alt="American Airlines Center" 
                style="width: 100%; max-width: 600px; margin-top: var(--space-4); border-radius: var(--border-radius-lg);"
            />
        </center>
    </div>

    <br>
    <center><h4 in:fly={{ y: 20, duration: 500, delay: 1900 }}> | </h4></center>
    <center><h4 in:fly={{ y: 20, duration: 500, delay: 2000 }}> | </h4></center>
    <center><h4 in:fly={{ y: 20, duration: 500, delay: 2100 }}> | </h4></center>
    <center><h4 in:fly={{ y: 20, duration: 500, delay: 2200 }}> | </h4></center>
    <center><h4 in:fly={{ y: 20, duration: 500, delay: 2300 }}> | </h4></center>
    <center><h4 in:fly={{ y: 20, duration: 500, delay: 2400 }}> | </h4></center>
    <center><h4 in:fly={{ y: 20, duration: 500, delay: 2500 }}> V </h4></center>

    <div class="meeting-info" in:fly={{ y: 20, duration: 600, delay: 2600 }}>
        <center><h1 style="color: var(--primary);">April 23, 2025</h1></center>
        <center><h3>The Forum</h3></center>
        <center><h5>Los Angeles, California</h5></center>
        <center>
            <img 
                src="concert locations/theforum.png" 
                alt="The Forum" 
                style="width: 100%; max-width: 600px; margin-top: var(--space-4); border-radius: var(--border-radius-lg);"
            />
        </center>
    </div>
</div>

<style>
    .hero {
        text-align: center;
        padding: var(--space-16) 0 0 0;
    }

    .hero h1 {
        margin-bottom: var(--space-4);
    }

    .meeting-info {
        display: flex;
        flex-direction: column;
        gap: var(--space-2);
    } 

    @media (max-width: 768px) {
        .hero {
            padding: var(--space-8) 0;
        }
    }
</style>