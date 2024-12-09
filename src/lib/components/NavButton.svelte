<script lang="ts">
    export let href = '';
    export let text = '';
</script>

<a {href} class="nav-button">
    {text}
</a>

<style>
    .nav-button {
        position: relative;
        display: inline-block;
        padding: 0.5rem 1rem;
        color: var(--text-secondary);
        text-decoration: none;
        font-weight: 500;
        letter-spacing: 0.05em;
        transition: color 0.3s var(--ease-in-out);
        z-index: 1;
    }

    .nav-button::before {
        content: '';
        position: absolute;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 2px;
        background: var(--color-primary);
        transform: scaleX(0);
        transform-origin: right;
        transition: transform 0.3s var(--ease-out);
        z-index: -1;
    }

    .nav-button:hover {
        color: var(--text-primary);
    }

    .nav-button:hover::before {
        transform: scaleX(1);
        transform-origin: left;
    }

    @media (max-width: 768px) {
        .nav-button {
            width: 100%;
            padding: 1rem;
            text-align: center;
            background: var(--bg-secondary);
            border-radius: var(--border-radius);
        }

        .nav-button:hover {
            background: var(--bg-primary);
            box-shadow: var(--shadow-sm);
        }
    }
</style>