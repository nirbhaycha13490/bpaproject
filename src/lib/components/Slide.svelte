<script lang="ts">
    export let src;
    export let date;
</script>

<div class="slide-card glass">
    <div class="slides-container">
        <object
            data="/meetings/{src}.pdf"
            type="application/pdf"
            width="100%"
            height="800"
        >
            <p>Unable to display PDF. <a href="/meetings/{src}.pdf" target="_blank">Download Instead</a></p>
        </object>
    </div>
    <div class="content">
        <div class="date">{date}</div>
        <a href="/meetings/{src}.pdf" target="_blank" class="view-button">View Full Screen</a>
    </div>
</div>

<style>
    .slide-card {
        display: flex;
        flex-direction: column;
        overflow: hidden;
        border-radius: var(--border-radius-xl);
        transition: transform var(--transition);
        background: rgba(18, 18, 18, 0.7);
    }

    

    .slides-container {
        width: 100%;
        height: 800px;
        overflow: hidden;
    }

    .slides-container object {
        border: none;
    }

    .content {
        padding: var(--space-6);
    }

    .date {
        color: var(--primary);
        font-size: var(--text-sm);
        margin-bottom: var(--space-2);
    }

    h3 {
        margin: 0 0 var(--space-2);
        font-size: var(--text-xl);
    }

    p {
        margin: 0 0 var(--space-4);
        color: var(--text-secondary);
        font-size: var(--text-base);
        line-height: 1.6;
    }

    .view-button {
        display: inline-flex;
        align-items: center;
        gap: var(--space-2);
        padding: var(--space-2) var(--space-4);
        background: var(--surface-200);
        color: var(--text-primary);
        text-decoration: none;
        border-radius: var(--border-radius-lg);
        font-size: var(--text-sm);
        transition: all var(--transition);
    }

    .view-button:hover {
        background: var(--primary);
        color: var(--surface-0);
        transform: translateY(-2px);
    }

    @media (max-width: 768px) {
        .slides-container {
            height: 500px;
        }
    }
</style>