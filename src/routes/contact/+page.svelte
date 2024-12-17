<script>
    import { fly } from 'svelte/transition';
    import { Mail, MapPin, Clock, Users } from 'lucide-svelte';
</script>

<div class="container">
    <section class="hero" in:fly={{ y: 20, duration: 600 }}>
        <h1 class="text-gradient">Contact Us</h1>
        <p class="subtitle">Get in touch with us</p>
    </section>

    <section class="contacts">
        <div class="contacts-grid">
            <div class="contact-card glass" in:fly={{ y: 20, duration: 600, delay: 100 }}>
                <div class="card-content">
                    <div class="icon-wrapper">
                        <Mail size={32} />
                    </div>
                    <h3>Email</h3>
                    <p style="line-height: 3.2;">stagefright202@gmail.com</p>
                    <a href="mailto:stagefright202@gmail.com" class="contact-button">
                        Send Email
                    </a>
                </div>
            </div>

            <div class="contact-card glass" in:fly={{ y: 20, duration: 600, delay: 200 }}>
                <div class="card-content">
                    <div class="icon-wrapper">
                        <MapPin size={32} />
                    </div>
                    <h3>Booking Link</h3>
                    <p>Schedule a meeting<br>with us</p>
                    <a href="https://www.signupgenius.com/go/10C0A45ACAC23A5FFC52-54084628-book#/" target="_blank" class="contact-button">
                        Book Meeting
                    </a>
                </div>
            </div>

            <div class="contact-card glass" in:fly={{ y: 20, duration: 600, delay: 300 }}>
                <div class="card-content">
                    <div class="icon-wrapper">
                        <Clock size={32} />
                    </div>
                    <h3>Customer Service Link</h3>
                    <p>Contact us for customer<br>service inquiries</p>
                    <a href="https://docs.google.com/forms/d/e/1FAIpQLSeTxmpwZYiYqzjs0vabLii3oflF6yFUi2OIw_Etk0050MZGOw/viewform?usp=header" target="_blank" class="contact-button">
                        View Schedule
                    </a>
                </div>
            </div>
 
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

    .contacts {
        padding-bottom: var(--space-16);
    }

    .contacts-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
        gap: var(--space-6);
    }

    .contact-card {
        border-radius: var(--border-radius-2xl);
        transition: transform var(--transition);
    }

    .card-content {
        padding: var(--space-8);
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: center;
        gap: var(--space-4);
    }

    .icon-wrapper {
        width: 64px;
        height: 64px;
        display: flex;
        align-items: center;
        justify-content: center;
        border-radius: 50%;
        background: var(--surface-200);
        margin-bottom: var(--space-2);
        color: var(--primary);
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

    .contact-button {
        background: var(--surface-200);
        color: var(--text-primary);
        text-decoration: none;
        padding: var(--space-2) var(--space-4);
        border-radius: var(--border-radius-lg);
        transition: all var(--transition);
        font-size: var(--text-sm);
    }

    .contact-button:hover {
        background: var(--primary);
        color: var(--surface-0);
        transform: translateY(-2px);
        box-shadow: 0 4px 12px var(--primary-hover);
    }


    @media (max-width: 768px) {
        .hero {
            padding: var(--space-8) 0;
        }

        .contacts {
            padding-bottom: var(--space-8);
        }

        .contacts-grid {
            gap: var(--space-4);
        }
    }
</style>
