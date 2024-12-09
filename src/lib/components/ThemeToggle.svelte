<script>
    import { onMount } from 'svelte';
    
    let theme = 'light';
    
    onMount(() => {
        const savedTheme = localStorage.getItem('theme') || 'light';
        theme = savedTheme;
        document.documentElement.setAttribute('data-theme', theme);
    });
    
    function toggleTheme() {
        theme = theme === 'light' ? 'dark' : 'light';
        document.documentElement.setAttribute('data-theme', theme);
        localStorage.setItem('theme', theme);
    }
</script>

<button
    class="theme-toggle"
    on:click={toggleTheme}
    aria-label="Toggle theme"
>
    {#if theme === 'light'}
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <path d="M12 3a6 6 0 0 0 9 9 9 9 0 1 1-9-9Z"/>
        </svg>
    {:else}
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <circle cx="12" cy="12" r="4"/>
            <path d="M12 2v2"/>
            <path d="M12 20v2"/>
            <path d="m4.93 4.93 1.41 1.41"/>
            <path d="m17.66 17.66 1.41 1.41"/>
            <path d="M2 12h2"/>
            <path d="M20 12h2"/>
            <path d="m6.34 17.66-1.41 1.41"/>
            <path d="m19.07 4.93-1.41 1.41"/>
        </svg>
    {/if}
</button>

<style>
    .theme-toggle {
        background: none;
        border: none;
        padding: 0.5rem;
        cursor: pointer;
        border-radius: 50%;
        color: var(--text-primary);
        transition: all 0.3s var(--ease-elastic);
    }

    .theme-toggle:hover {
        transform: scale(1.1) rotate(15deg);
        background: var(--surface-hover);
    }

    .theme-toggle:active {
        transform: scale(0.9);
    }
</style>
