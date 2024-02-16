<script lang="ts">
	import { addToast } from '$lib/components/Toast.svelte';

	function toast() {
		addToast({
			data: {
				title: 'Success',
				description: 'The resource was created!',
				color: 'green'
			}
		});
	}
</script>

<button on:click={toast}>Show toast</button>

<style>
	button {
		background-color: var(--surface0);
		border: thin solid var(--surface0);
		border-radius: 8px;
		color: var(--text);
		cursor: pointer;
		display: inline-flex;
		font-size: 1rem;
		padding: 0.6rem 1.2rem;
		transition:
			background-color 0.2s ease-in-out,
			border-color 0.2s ease-in-out;
	}

	button:hover {
		background-color: var(--surface1);
		border-color: var(--surface1);
	}
</style>
