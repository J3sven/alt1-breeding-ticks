<script>
<<<<<<< HEAD
	export let name;
</script>

<main>
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
=======
	import Clock from './Clock.svelte';
</script>

<main>
	<p>Build tick app</p>

	<Clock />

>>>>>>> parent of 082673a... switched to sveltekit
</main>

<style>
	main {
<<<<<<< HEAD
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
=======
		padding: 0;
		max-width: 240px;
		margin: 0;
		background-color: #1C2C34;
		color: white;
		min-height: 100vh;
		min-width: 100vw;
>>>>>>> parent of 082673a... switched to sveltekit
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>