<script lang="ts">
	import Slide from "$lib/components/Slide.svelte";
</script>

<div class="container">
	<div id="schedule">
		<div>
			<h1>Next Meeting</h1>
			<h2>January 1, 1970</h2>
			<h2>Mr. Patton's room (B213) @ Adv'</h2>
		</div>
		<div>
			<h1>Next Competition</h1>
			<h2>None</h2>
		</div>
	</div>
	<br/>
	<h1>Past Meeting Slides</h1>
	<div id="slides">
		<Slide src="10-10-2024" date="October 10, 2024" />
		<Slide src="10-10-2024" date="October 10, 2024" />
	</div>
</div>

<style>
	#schedule {
		display: flex;
		justify-content: space-evenly;
	}

	#schedule h1 {
		line-height: 25px;
		margin-top: 30px;
		margin-bottom: 10px;
	}

	h2 {
		margin: 0;
	}

	#slides {
		display: inline-grid;
		grid-template-columns: auto auto;
		gap: 60px 100px;
		justify-content: middle;
	}
</style>