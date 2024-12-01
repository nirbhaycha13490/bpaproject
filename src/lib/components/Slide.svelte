<script lang="ts">
	let { src, date } = $props();
</script>

<div>
	<embed class="pdf" src="/meetings/{ src }.pdf" width="640px" height="360px" />
	<a href="/meetings/{src}.pdf" target="_blank"><h1>{ date }</h1></a>
</div>

<style>
	.pdf {
		margin: 0;
	}

	h1 {
		margin: 0;
		font-family: Rubik;
	}

	a {
		color: linear-gradient(90deg, var(--blue), var(--green));
	}
</style>