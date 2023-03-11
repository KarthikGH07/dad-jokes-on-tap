<script lang="ts">
	import { onMount } from 'svelte';
	import Button from '../lib/Button.svelte';

	type Joke = { id: string; joke: string; status: number };

	let loading = false;
	let joke = '';

	const randomJoke = async () => {
		try {
			loading = true;
			const res = await fetch('https://icanhazdadjoke.com/', {
				headers: { Accept: 'application/json' }
			});
			const data: Joke = await res.json();
			joke = data.joke;
			loading = false;
		} catch (error) {
			loading = false;
		}
	};

	onMount(randomJoke);
</script>

<div class="card">
	<h2 class="joke">{!loading ? joke : 'Loading...'}</h2>
	<Button {loading} handleClick={randomJoke}>New Joke!</Button>
</div>

<style>
	.card {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		gap: 3rem;
		background-color: #f1f9f9;
		width: 55vw;
		/* height: 408px; */
		min-height: fit-content;
		border-radius: 0.5rem;
		padding: 5vw;
		box-shadow: 0px 301px 84px rgba(15, 42, 41, 0.01), 0px 192px 77px rgba(15, 42, 41, 0.06),
			0px 108px 65px rgba(15, 42, 41, 0.2), 0px 48px 48px rgba(15, 42, 41, 0.34),
			0px 12px 26px rgba(15, 42, 41, 0.39), 0px 0px 0px rgba(15, 42, 41, 0.4);
	}
	.joke {
		font-family: 'Rubik';
		font-style: normal;
		font-weight: 400;
		font-size: 3rem;
		line-height: 3rem;
		color: #0f2a29;
	}

	@media screen and (max-width: 768px) {
		.card {
			width: 90vw;
		}
	}

	@media screen and (max-width: 425px) {
		.card {
			width: 100%;
			box-shadow: none;
			border-radius: 0;
		}
	}
</style>
