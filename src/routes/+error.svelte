<script>
	import { page } from '$app/stores';
</script>

<div class="container">
	<h1>ERROR {$page.status}</h1>
	<h2>{$page.error?.message}</h2>
</div>