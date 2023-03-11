<script lang="ts">
	import '../app.css';
</script>

<main>
	<slot />
</main>

<style>
	main {
		background-color: #005450;
		height: 100dvh;
		display: grid;
		place-items: center;
	}

	@media screen and (max-width: 425px) {
		main {
			background-color: #f1f9f9;
			display: block;
		}
	}
</style>
