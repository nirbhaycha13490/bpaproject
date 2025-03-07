<script lang="ts">
    import { fly } from 'svelte/transition';
    import { Tag, Plus, Minus } from 'lucide-svelte';
	import { browser } from '$app/environment';

	function getSessionStorage(field: string) {
		if (browser) return window.sessionStorage.getItem(field);
	}

	function setSessionStorage(field: string, value: string) {
		if (browser) return window.sessionStorage.setItem(field, value);
	}

    interface ProductCard {
        name: string,
        price: number,
        description: string,
        image: string,
        sizes: string[]
    }

    const products: ProductCard[] = [
        {
            name: 'T-Shirt',
            price: 8.99,
            description: 'Red t-shirt',
            image: "shop/stshirt1.png",
            sizes: ['S', 'M', 'L', 'XL'],
            //id: '675a08763ac33',
        },
		{
            name: 'T-Shirt',
            price: 8.99,
            description: 'Black t-shirt',
            image: "shop/stshirt2.png",
            sizes: ['S', 'M', 'L', 'XL'],
            //id: '675a08763ac33',
        },
        {
            name: 'Shorts',
            price: 4.99,
            description: 'Light Gray shorts',
            image: "shop/stshorts.png",
            sizes: ['S', 'M', 'L', 'XL'],
            //id: '675a0887a0102',
        },
        {
            name: 'Quarter Zip',
            price: 11.99,
            description: 'Black Quarter Zip',
            image: "shop/stsweatshirt.png",
            sizes: ['S', 'M', 'L', 'XL'],
            //id: '675a088b74d4e',
        },
        {
            name: 'Pants',
            price: 8.00,    
            description: 'Black sweatpants',
            image: "shop/stsweatpants.png",
            sizes: ['S', 'M', 'L', 'XL'],
            //id: '675a0ae01ac60',
        },
        {
            name: 'Hoodie',
            price: 8.00,    
            description: 'Dark Gray Hoodie ',
            image: "shop/sthoodie.png",
            sizes: ['S', 'M', 'L', 'XL'],
            //id: '675a0bd184ef7',
        },
    ];

    interface ShopItem {
        index: number,
        size: string,
        qty: number
    }

	let checkout: ShopItem[] = JSON.parse(getSessionStorage("checkout") || "[]");
	console.log(checkout);
	let total = 0;

	function updateTotal() {
		setSessionStorage('checkout', JSON.stringify(checkout));
		total = 0;

		for (const item of checkout) {
			total += products[item.index].price * item.qty;
		}
	}
	updateTotal();

    function addItem(index: number, size: string) {
        // If we are buying two of the same items, then combine the items
        for (let i = 0; i < checkout.length; i++) {
            if (checkout[i].index === index && checkout[i].size === size) {
                checkout[i].qty = Math.min(checkout[i].qty + 1, 10);
				updateTotal();
                return;
            }
        }

        checkout.push({ index: index, size: size, qty: 1 });
        checkout = checkout; // To make checkout reactive
		updateTotal();
    }

    function addQty(index: number, amount: number) {
        checkout[index].qty = Math.min(checkout[index].qty + amount, 10);
        if (checkout[index].qty <= 0) checkout.splice(index, 1);
		updateTotal();
    }

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
        <h1 class="text-gradient">Merch Store</h1>
        <p class="subtitle">Support our band and get awesome gear</p>
    </section>

	<section style="text-align: center; margin-bottom: var(--space-16);">
		<div class="checkout" in:fly={{ y: 20, duration: 600 }}>
			<h2>Shopping Cart</h2>
            {#if checkout.length === 0}<p transition:fly={{ y: -30, duration: 600 }}>You haven't added anything yet!</p>{/if}
			<div class="checkout-grid">
				{#each checkout as item, i}
					<div class="checkout-item glass" transition:fly|global={{ y: 20, duration: 600 }}>
						<img src={products[item.index].image} alt="Icon"/>
						<div class="checkout-item-right">
							<div class="checkout-item-top">
								<h3>{products[item.index].name}</h3>
								<h3 style="color: var(--primary);">${(products[item.index].price * item.qty).toFixed(2)}</h3>
							</div>
							<div class="checkout-item-bottom">
								<p style="margin: 0;">Size {item.size}</p>
								<div class="checkout-qty">
									<button class="checkout-qty-decrease" onclick={() => addQty(i, -1)}>
										<div class="feature-icon"><Minus size={24} /></div>
									</button>
									<h3>{item.qty}</h3>
									<button class="checkout-qty-increase" onclick={() => addQty(i, 1)}>
										<div class="feature-icon"><Plus size={24} /></div>
									</button>
								</div>
							</div>
						</div>
					</div>
				{/each}
			</div>
            {#if checkout.length > 0}
                <div><!-- prevent inline-flex from flexing the parent divs -->
					<div class="process" transition:fly={{ y: 40, duration: 600 }}>
						<h3>Total: ${total.toFixed(2)} + Tax</h3>
                    	<button class="buy-button">Checkout</button>
					</div>
                </div>
            {/if}
		</div>
	</section>

    <section class="products">
        <div class="products-grid">
            {#each products as product, i}
                <div class="product-card glass" in:fly|global={{ y: 20, duration: 600, delay: (i + 1) * 100 }}>
                    <div class="product-image">
                        <img src={product.image} alt={product.description} />
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
                                    <button class="size-button" onclick={() => addItem(i, size)}>{size}</button>
                                {/each}
                            </div>
                        {/if}
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
		font-size: var(--text-base);
		font-family: inherit;
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
        transition: all var(--transition);
		padding: var(--space-6);
		display: inline-flex;
    }

	.checkout {
		text-align: center;
        display: block;
	}

    .checkout > p {
        position: absolute;
        margin: auto;
        left: 0;
        right: 0;
    }

    .checkout-grid {
        display: grid;
        position: relative;
		gap: var(--space-4);
		grid-template-columns: repeat(auto-fit, minmax(300px, 350px));
		margin-bottom: var(--space-4);
		justify-content: center;
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
        padding: 0;
	}

	.checkout-qty > button:hover {
        background: var(--primary);
		box-shadow: 0 4px 12px var(--primary-hover);
		color: var(--surface-0);
    }

	.feature-icon {
        display: flex;
        justify-content: center;
        color: inherit;
    }

	.checkout-item img {
		height: 60px;
		width: 60px;
		border-radius: 50%;
        padding: 0;
        margin: 0;
        aspect-ratio: 1;
        margin-right: var(--space-6);
        align-self: center;
	}

	.process {
		display: inline-flex
	}

	.process > h3 {
		color: var(--primary);
		text-wrap: nowrap;
		margin: auto var(--space-4) auto 0;
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
