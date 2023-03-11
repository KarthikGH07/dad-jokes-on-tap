<script lang="ts">
	export let loading = false;
	export let handleClick: () => void;
</script>

<button on:click={handleClick} disabled={loading}>
	<slot />
</button>

<style>
	button {
		display: flex;
		align-items: center;
		padding: 1em 2em;
		background: #faba5b;
		border-radius: 6px;
		font-family: 'Rubik';
		font-style: normal;
		font-weight: 500;
		font-size: 1rem;
		line-height: 1.5rem;
		color: #543200;
		border: none;
		cursor: pointer;
		outline: none;
	}

	button:hover {
		background: #f89b0f;
	}

	button:disabled {
		background: #f89b0f;
		opacity: 0.7;
	}

	button:focus {
		border: 2px solid #faba5b;
	}
</style>
