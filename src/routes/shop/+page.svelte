<script>
    import { fly } from 'svelte/transition';
    import { ShoppingCart, Tag, Box, Plus, Minus } from 'lucide-svelte';

    const products = [
        {
            name: 'T-Shirt',
            price: 8.99,
            description: 'Blue cotton t-shirt',
            image: "shop/shirt1.png",
            sizes: ['S', 'M', 'L', 'XL'],
            //id: '675a08763ac33',
			delay: 0
        },
		{
            name: 'Shirt',
            price: 8.99,
            description: 'Yellow cotton shirt',
            image: "shop/shirt2.png",
            sizes: ['S', 'M', 'L', 'XL'],
            //id: '675a08763ac33',
			delay: 0
        },
        {
            name: 'Shorts',
            price: 4.99,
            description: 'Blue cotton shorts',
            image: "shop/pants1.png",
            sizes: ['S', 'M', 'L', 'XL'],
            //id: '675a0887a0102',
			delay: 0
        },
        {
            name: 'Sweater',
            price: 11.99,
            description: 'Grey sweatshirt',
            image: "shop/sweatshirt1.png",
            sizes: ['S', 'M', 'L', 'XL'],
            //id: '675a088b74d4e',
			delay: 0
        },
        {
            name: 'Pants',
            price: 8.00,    
            description: 'Light grey sweatpants',
            image: "shop/sweatpants1.png",
            sizes: ['S', 'M', 'L', 'XL'],
            //id: '675a0ae01ac60',
			delay: 0
        },
        {
            name: 'Hoodie',
            price: 8.00,    
            description: 'White hoodie sweatshirt',
            image: "shop/hoodie1.png",
            sizes: ['S', 'M', 'L', 'XL'],
            //id: '675a0bd184ef7',
			delay: 0
        },
    ];

	for (let i = 0; i < products.length; i++) {
		products[i].delay = (i + 1) * 100;
	}

	let checkout = [
		{
			item: "Shirt",
			index: 1,
			size: "XL",
			qty: 2
		},
		{
			item: "White hoodie sweatshirt",
			index: 2,
			size: "XL",
			qty: 2
		}
	];

    // // Load Sellix Embed Scripts Dynamically
    // if (typeof window !== 'undefined') {
    //     const sellixScript = document.createElement('script');
    //     sellixScript.src = "https://cdn.sellix.io/static/js/embed.js";
    //     sellixScript.async = true;
    //     document.head.appendChild(sellixScript);

    //     const sellixStyle = document.createElement('link');
    //     sellixStyle.rel = "stylesheet";
    //     sellixStyle.href = "https://cdn.sellix.io/static/css/embed.css";
    //     document.head.appendChild(sellixStyle);
    // }
</script>


<div class="container">
    <section class="hero" in:fly={{ y: 20, duration: 600 }}>
        <h1 class="text-gradient">Club Shop</h1>
        <p class="subtitle">Support our club and get awesome gear</p>
    </section>

    <section class="products">
        <div class="products-grid">
            {#each products as product}
                <div class="product-card glass" in:fly|global={{ y: 20, duration: 600, delay: product.delay }}>
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

                        <!-- <button class="buy-button"
                            data-sellix-product="{product.id}"
                            type="submit"
                            alt="Buy Now with sellix.io">
                            Purchase
                        </button> -->
						<button class="buy-button" type="submit">Purchase</button>
                    </div>
                </div>
            {/each}
        </div>
    </section>

    <!-- <section class="info">
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
    </section> -->

	<section style="text-align: center;">
		<div class="checkout" in:fly={{ y: 20, duration: 600 }}>
			<h2>Checkout</h2>
			<div class="checkout-grid">
				{#each checkout as item}
					<div class="checkout-item glass">
						<img src={products[item.index].image} alt="Icon"/>
						<div class="checkout-item-right">
							<div class="checkout-item-top">
								<h3>{item.item}</h3>
								<h3 style="color: var(--primary);">${products[item.index].price * item.qty}</h3>
							</div>
							<div class="checkout-item-bottom">
								<p style="margin: 0;">Size {item.size}</p>
								<div class="checkout-qty">
									<button class="checkout-qty-decrease">
										<Minus class="feature-icon" />
									</button>
									<h3>{item.qty}</h3>
									<button class="checkout-qty-increase">
										<Plus class="feature-icon" />
									</button>
								</div>
							</div>
						</div>
					</div>
				{/each}
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
		max-width: 900px;
		margin: auto;
    }

    .product-card {
        border-radius: var(--border-radius-2xl);
        overflow: hidden;
        transition: transform var(--transition);
    }

    .product-image {
        position: relative;
        width: 100%;
		aspect-ratio: 1;
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
        box-shadow: 0 4px 12px var(--primary-hover);
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

	.checkout h2 {
		text-align: center;
		margin-bottom: var(--space-6);
        font-size: var(--text-2xl);
    }

	.checkout-item {
        border-radius: var(--border-radius-2xl);
        overflow: hidden;
        transition: transform var(--transition);
		padding: var(--space-6);
		display: flex;
		gap: var(--space-6);
		margin-bottom: var(--space-2);
    }

	.checkout {
		display: inline-block;
		text-align: left;
	}

	.checkout-item-right {
		width: 100%;
	}

	.checkout-item-right > div {
		display: flex;
		gap: var(--space-6);
		flex-grow: 1;
	}

	.checkout-item-top {
		margin-bottom: var(--space-2);
		justify-content: space-between;
	}

	.checkout-item-bottom {
		display: flex;
		justify-content: space-between;
	}

	.checkout-qty {
		display: flex;
		gap: var(--space-4);
	}

	.checkout-qty h3 {
		margin: auto;
		font-size: 24px;
	}

	.checkout-qty > button {
		width: 32px;
		height: 32px;
		border-radius: 50%;
		border: none;
		background: var(--surface-200);
		transition: all var(--transition);
		color: var(--text-primary);
		cursor: pointer;
	}

	.checkout-qty > button:hover {
        background: var(--primary);
		box-shadow: 0 4px 12px var(--primary-hover);
		color: var(--surface-0);
    }

	.feature-icon {
        width: 100%;
        height: 100%;
        margin: 0 auto var(--space-4);
        display: flex;
        align-items: center;
        justify-content: center;
        color: inherit;
    }

	.checkout-item img {
		height: 60px;
		width: 60px;
		border-radius: 50%;
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
