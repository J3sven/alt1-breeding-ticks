<script>
	import Clock from './Clock.svelte';
</script>

<main>
	<p>Build tick app</p>

	<Clock />

</main>

<style>
	main {
		padding: 0;
		max-width: 240px;
		margin: 0;
		background-color: #1C2C34;
		color: white;
		min-height: 100vh;
		min-width: 100vw;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>