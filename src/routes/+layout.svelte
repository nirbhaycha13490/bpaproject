<script lang="ts">
	let { children } = $props();
	import "../app.css";
	import NavButton from "$lib/components/NavButton.svelte";
</script>

<nav id="navbar">
	<div id="header-logo">
		<a href="/"><img src="/logo.png" id="header-icon" alt="Home"/></a>
		<h1 id="header-title">Reedy<br/>Engineering<br/>Club</h1>
	</div>
	<div id="header-nav">
		<NavButton to="/" text="Home" />
		<NavButton to="/about" text="About" />
		<NavButton to="/meetings" text="Meetings" />
		<NavButton to="/shop" text="Shop" />
		<NavButton to="/contact" text="Contact" />
	</div>
</nav>

{@render children()}

<style>
	#navbar {
		background-image: linear-gradient(90deg, var(--blue), var(--green));
		display: flex;
		color: white;
		width: 100%;
		height: 80px;
		text-shadow: 2px 2px 2px rgb(0, 0, 0, 25%);
		-webkit-text-stroke: 4px black;
		paint-order: stroke fill;
		text-align: left;
		position: fixed;
	}

	#header-logo {
		display: flex;
		align-items: center;
	}

	#header-icon {
		margin: 6px 4px 2px 10px;
		width: 60px;
	}

	#header-title {
        font-size: 20px;
		letter-spacing: 5px;
		line-height: 20px;
    }

	#header-nav {
		display: flex;
		margin-left: auto;
	}
</style>