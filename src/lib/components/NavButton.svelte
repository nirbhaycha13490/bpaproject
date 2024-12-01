<script lang="ts">
	import { page, navigating } from '$app/stores';
	let { to, text } = $props();

	function getBgStyle() {
		return $page.url.pathname === to ? "background: rgb(0, 0, 0, 25%);" : null;
	}
	let current = $state(getBgStyle());
	$effect(() => { if($navigating) current = getBgStyle(); });
</script>

<button class="nav-button" style={current}>
	<a class="nav-a" href={to}>{text}</a>
</button>

<style>
	.nav-button {
		height: 48px;
		background: transparent;
		border: none;
		border-radius: 10px;
		padding: 0;
		margin: auto 8px;
		transition: 0.25s;
	}

	.nav-button:hover {
		background: rgb(0, 0, 0, 25%);
	}

	.nav-a {
		color: white;
		text-decoration: none;
		font-size: 24px;
		font-family: Rubik Mono One;
		width: 100%;
		height: 100%;
		padding: 0 16px;
		text-shadow: 2px 2px 2px rgb(0, 0, 0, 25%);
		-webkit-text-stroke: 4px black;
	}
</style>