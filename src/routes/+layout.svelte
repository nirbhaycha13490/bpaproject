<script>
    import "../app.css";
    import { onMount } from 'svelte';
    import { fade, fly } from 'svelte/transition';
    import { page } from '$app/stores';

    let isMenuOpen = false;
    let isScrolled = false;
    let mounted = false;

    onMount(() => {
        mounted = true;
        const handleScroll = () => {
            isScrolled = window.scrollY > 20;
        };
        window.addEventListener('scroll', handleScroll);
        return () => window.removeEventListener('scroll', handleScroll);
    });

    let previousRoute = "/";

    $: {
        if (previousRoute !== $page.url.pathname) {
            previousRoute = $page.url.pathname;
            isMenuOpen = false;
        }
    }
</script>

<div class="layout">
    <header class:scrolled={isScrolled} class="glass">
        <nav class="container">
            <a href="/" class="logo">
                <div class="logo-container">
                    <span class="text-gradient" style="font-size: 30px;">Stage Fright</span>

                </div>
            </a>

            <div class="nav-links" class:open={isMenuOpen}>
                <a href="/" class="nav-link">Home</a>
                <a href="/about" class="nav-link">About</a>
                <a href="/meetings" class="nav-link">Tour Dates</a>
                <a href="/shop" class="nav-link">Merch</a>
                <a href="/contact" class="nav-link">Contact</a>
            </div>

            <button 
                class="menu-toggle" 
                on:click={() => isMenuOpen = !isMenuOpen}
                aria-label="Toggle menu"
            >
                <div class="menu-icon" class:open={isMenuOpen}>
                    <span></span>
                    <span></span>
                    <span></span>
                </div>
            </button>
        </nav>
    </header>

    <main>
        {#if mounted}
            <div in:fly={{ y: 20, duration: 800, delay: 200 }} out:fade>
                <slot />
            </div>
        {/if}
    </main>

    <footer class="glass">
        <div class="container">
            <div class="footer-content">
                <div class="footer-section">
                    <h3>
                        <span class="text-gradient" style="font-size: var(--text-2xl)">Stage Fright</span>
                    </h3>
                    <p>Rock for the Masses</p>
                    <div class="social-links">
                        <a href="https://www.instagram.com/stage_fright202/profilecard/?igsh=MXYzNHBqdDRwdDJzbw==" target="_blank" rel="noopener" aria-label="Instagram" class="glass-hover">
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                                <rect width="20" height="20" x="2" y="2" rx="5" ry="5"/>
                                <path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"/>
                                <line x1="17.5" x2="17.51" y1="6.5" y2="6.5"/>
                            </svg>
                        </a>
                        <a href="https://www.tiktok.com/@stage.fright4?_t=ZP-8sHesua5oa6&_r=1" target="_blank" rel="noopener" aria-label="TikTok" class="glass-hover">
                            <img src="socials/TikTok.png" alt = tiktok width="40" height="24" style="color: var(--text-secondary)" />
                        </a>
                        <a href="mailto:stagefright202@gmail.com" aria-label="Email" class="glass-hover">
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                                <rect width="20" height="16" x="2" y="4" rx="2"/>
                                <path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/>
                            </svg>
                        </a>
						
                    </div>
                </div>
                <div class="footer-section">
                    <h4 style="font-size: 20px; font-weight: bold;">BPA Information</h4>
                    <p style="font-size: 12px; line-height: 1.5;"><strong>Chapter Name:</strong> Reedy High School BPA (Chapter 02-1308)</p>
                    <p style="font-size: 12px; line-height: 1.5;"><strong>Team Members:</strong> Saksham Shukla, Nirbhay Challa, Aarnav Thakur</p>
                    <p style="font-size: 12px; line-height: 1.5;"><strong>Theme:</strong> Stage Fright Rock Band</p>
                    <p style="font-size: 12px; line-height: 1.5;"><strong>School:</strong> Reedy High School</p>
                    <p style="font-size: 12px; line-height: 1.5;"><strong>City, State:</strong> Frisco, TX</p>
                    <p style="font-size: 12px; line-height: 1.5;"><strong>Year:</strong> 2024</p>
                </div>
                
                
                <div class="footer-section">
                    <h4>Quick Links</h4>
                    <a href="/" class="hover-lift">Home</a>
                    <a href="/about" class="hover-lift">About</a>
                    <a href="/meetings" class="hover-lift">Tour Dates</a>
                    <a href="/shop" class="hover-lift">Merch</a>
                    <a href="/contact" class="hover-lift">Contact</a>
                </div>
                <div class="footer-section">
                    <h4>Contact Us</h4>
                    <p style="font-size: 0.9em;">Email: stagefright202@gmail.com</p>
                    <p style="font-size: 0.9em;">Phone: 469-588-5791</p>
                    <p style="font-size: 0.9em;">Address: 123 Maplewood Drive, Frisco, TX 62704</p>


                </div>
            </div>
            <div class="footer-bottom">
                <p>Stage Fright | All rights reserved.</p>
            </div>
        </div>
    </footer>
</div>

<style>
    
    .layout {
        display: flex;
        flex-direction: column;
        min-height: 100vh;
    }

    header {
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        height: var(--nav-height);
        z-index: 100;
        padding: var(--space-4) 0;
		/*backdrop-filter: blur(12px);*/
        border: 1px solid var(--glass-border);
        box-shadow: 0 -4px 30px rgba(0, 0, 0, 0.1);
    }

    nav {
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .logo {
        text-decoration: none;
        z-index: 100;
    }

    .logo-container {
        display: flex;
        align-items: center;
    }

    .text-gradient {
        font-size: var(--text-xl);
        font-weight: 500;
        line-height: 1;
    }

    .nav-links {
        display: flex;
        gap: var(--space-8);
        padding: var(--space-3) var(--space-6);
        border-radius: var(--border-radius-2xl);
        background: var(--surface-100);
    }

    .nav-link {
        color: var(--text-primary);
        text-decoration: none;
        transition: color var(--transition);
    }

    .nav-link:hover {
        color: var(--primary);
    }

    .menu-toggle {
        display: none;
        background: none;
        border: none;
        cursor: pointer;
        padding: var(--space-2);
    }

    .menu-icon {
        width: 24px;
        height: 18px;
        position: relative;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }

    .menu-icon span {
        width: 100%;
        height: 2px;
        background: var(--text-primary);
        transition: transform var(--transition);
    }

    .menu-icon.open span:first-child {
        transform: translateY(8px) rotate(45deg);
    }

    .menu-icon.open span:nth-child(2) {
        opacity: 0;
    }

    .menu-icon.open span:last-child {
        transform: translateY(-8px) rotate(-45deg);
    }

    main {
        flex: 1;
        margin-top: calc(var(--nav-height) + var(--space-8));
    }

    footer {
        margin-top: var(--space-16);
        border: 1px solid var(--glass-border);
    }
    .footer-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: var(--space-6);
            flex-wrap: nowrap; 
            padding: var(--space-12) 0 var(--space-6) 0;
            overflow: hidden; 
        }




    

    .footer-section {
        display: flex;
        flex-direction: column;
        gap: var(--space-4);
    }

    .footer-section h3 {
        display: flex;
        gap: var(--space-2);
        font-size: var(--text-2xl);
        margin-bottom: var(--space-2);
    }

    .footer-section h4 {
        font-size: var(--text-lg);
        color: var(--text-primary);
        margin-bottom: var(--space-2);
    }

    .footer-section p {
        color: var(--text-secondary);
		margin: 0;
    }

    .social-links {
        display: flex;
        gap: var(--space-4);
        margin-top: var(--space-4);
    }

    .social-links a {
        display: flex;
        align-items: center;
        justify-content: center;
        min-width: 40px;
        height: 40px;
        color: var(--text-primary);
        border-radius: var(--border-radius-lg);
        transition: all 0.3s ease;
    }

    .footer-section a {
        color: var(--text-secondary);
        text-decoration: none;
        transition: all 0.2s ease;
    }

    .footer-bottom {
        padding: 0 0 var(--space-6) 0;
        border-top: 1px solid var(--glass-border);
        text-align: center;
        color: var(--text-tertiary);
    }

    @media (max-width: 768px) {
        .nav-links {
            position: fixed;
            top: calc(var(--nav-height) + var(--space-4));
            left: var(--space-4);
            right: var(--space-4);
            flex-direction: column;
            align-items: center;
            padding: var(--space-4);
            transform: translateY(-1rem);
            opacity: 0;
            pointer-events: none;
            transition: all var(--transition);
        }

        .nav-links.open {
            transform: translateY(0);
            opacity: 1;
            pointer-events: all;
        }

        .menu-toggle {
            display: block;
        }

        .footer-content {
            grid-template-columns: 1fr;
            gap: var(--space-8);
            text-align: center;
        }

        .footer-section {
            align-items: center;
        }

        .social-links {
            justify-content: center;
        }

        .footer-section h3 {
            justify-content: center;
        }
        

    }
</style>