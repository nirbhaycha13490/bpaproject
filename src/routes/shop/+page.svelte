<script>
    import { fly } from 'svelte/transition';
    import { ShoppingCart, Tag, Box } from 'lucide-svelte';

    const products = [
        {
            name: 'product 1',
            price: 20,
            description: 'placeholder',
            image: '/projects/placeholder.jpg',
            sizes: ['S', 'M', 'L', 'XL']
        },
        {
            name: 'product 2',
            price: 35,
            description: 'placeholder',
            image: '/projects/placeholder.jpg',
            type: 'Kit'
        },
        {
            name: 'product 3',
            price: 5,
            description: 'placeholder',
            image: '/projects/placeholder.jpg',
            type: 'Accessories'
        },
        {
            name: 'product 4',
            price: 25,
            description: 'placeholder',
            image: '/projects/placeholder.jpg',
            type: 'Materials'
        }
    ];
</script>

<div class="container">
    <section class="hero">
        <h1 class="text-gradient">Club Shop</h1>
        <p class="subtitle">Support our club and get awesome gear</p>
    </section>

    <section class="products">
        <div class="products-grid">
            {#each products as product}
                <div class="product-card glass" in:fly={{ y: 20, duration: 600 }}>
                    <div class="product-image">
                        <img src={product.image} alt={product.name} />
                        <div class="price-tag">
                            <Tag size={16} />
                            <span>${product.price}</span>
                        </div>
                    </div>
                    <div class="product-content">
                        <h3>{product.name}</h3>
                        <p>{product.description}</p>
                        {#if product.sizes}
                            <div class="sizes">
                                {#each product.sizes as size}
                                    <button class="size-button">{size}</button>
                                {/each}
                            </div>
                        {/if}
                        {#if product.type}
                            <div class="type-tag">
                                <Box size={16} />
                                <span>{product.type}</span>
                            </div>
                        {/if}
                        <button class="buy-button">
                            <ShoppingCart size={16} />
                            Add to Cart
                        </button>
                    </div>
                </div>
            {/each}
        </div>
    </section>

    <section class="info">
        <div class="info-content glass" in:fly={{ y: 20, duration: 600 }}>
            <h2>How to Order</h2>
            <div class="info-grid">
                <div class="info-card">
                    <h3>1. Select Items</h3>
                    <p>Choose your items and desired sizes/options</p>
                </div>
                <div class="info-card">
                    <h3>2. Place Order</h3>
                    <p>Fill out the order form with your details</p>
                </div>
                <div class="info-card">
                    <h3>3. Payment</h3>
                    <p>Pay during the next club meeting</p>
                </div>
                <div class="info-card">
                    <h3>4. Pickup</h3>
                    <p>Collect your items at the following meeting</p>
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

    .products {
        padding-bottom: var(--space-16);
    }

    .products-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
        gap: var(--space-6);
    }

    .product-card {
        border-radius: var(--border-radius-2xl);
        overflow: hidden;
        transition: transform var(--transition);
    }

    .product-card:hover {
        transform: translateY(-4px);
    }

    .product-image {
        position: relative;
        width: 100%;
        height: 200px;
        overflow: hidden;
    }

    .product-image img {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

    .price-tag {
        position: absolute;
        top: var(--space-4);
        right: var(--space-4);
        background: var(--surface-0);
        color: var(--text-primary);
        padding: var(--space-2) var(--space-3);
        border-radius: var(--border-radius-lg);
        display: flex;
        align-items: center;
        gap: var(--space-2);
        font-weight: 500;
    }

    .product-content {
        padding: var(--space-6);
    }

    h3 {
        margin: 0 0 var(--space-2);
        font-size: var(--text-xl);
    }

    p {
        color: var(--text-secondary);
        margin: 0 0 var(--space-4);
        line-height: 1.6;
    }

    .sizes {
        display: flex;
        gap: var(--space-2);
        margin-bottom: var(--space-4);
    }

    .size-button {
        background: var(--surface-200);
        border: none;
        color: var(--text-primary);
        padding: var(--space-2) var(--space-3);
        border-radius: var(--border-radius-lg);
        cursor: pointer;
        transition: all var(--transition);
    }

    .size-button:hover {
        background: var(--primary);
        color: var(--surface-0);
    }

    .type-tag {
        display: inline-flex;
        align-items: center;
        gap: var(--space-2);
        background: var(--surface-200);
        color: var(--text-primary);
        padding: var(--space-2) var(--space-3);
        border-radius: var(--border-radius-lg);
        margin-bottom: var(--space-4);
    }

    .buy-button {
        width: 100%;
        background: var(--primary);
        color: var(--surface-0);
        border: none;
        padding: var(--space-3) var(--space-4);
        border-radius: var(--border-radius-lg);
        cursor: pointer;
        font-weight: 500;
        display: flex;
        align-items: center;
        justify-content: center;
        gap: var(--space-2);
        transition: all var(--transition);
    }

    .buy-button:hover {
        transform: translateY(-2px);
        box-shadow: 0 4px 12px rgba(0, 209, 255, 0.3);
    }

    .info {
        padding-bottom: var(--space-16);
    }

    .info-content {
        padding: var(--space-8);
        border-radius: var(--border-radius-2xl);
        text-align: center;
    }

    .info-content h2 {
        margin-bottom: var(--space-8);
        font-size: var(--text-2xl);
    }

    .info-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
        gap: var(--space-6);
    }

    .info-card h3 {
        color: var(--primary);
        margin-bottom: var(--space-2);
    }

    @media (max-width: 768px) {
        .hero {
            padding: var(--space-8) 0;
        }

        .products {
            padding-bottom: var(--space-8);
        }

        .info {
            padding-bottom: var(--space-8);
        }

        .info-grid {
            gap: var(--space-4);
        }
    }
</style>
