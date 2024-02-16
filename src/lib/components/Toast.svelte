<script lang="ts" context="module">
	import Cross from '$lib/icons/Cross.svelte';
	import { flip } from 'svelte/animate';
	import { fly } from 'svelte/transition';

	export type ToastData = {
		title: string;
		description: string;
		color: string;
	};

	const {
		elements: { content, title, description, close },
		helpers,
		states: { toasts },
		actions: { portal }
	} = createToaster<ToastData>();

	export const addToast = helpers.addToast;
</script>

<script lang="ts">
	import { createToaster } from '@melt-ui/svelte';
</script>

<div class="container" use:portal>
	{#each $toasts as { id, data } (id)}
		<div
			{...$content(id)}
			use:content
			animate:flip={{ duration: 500 }}
			in:fly={{ duration: 150, x: '100%' }}
			out:fly={{ duration: 150, x: '100%' }}
			class="layout"
		>
			<div class="banner">
				<h3 {...$title(id)} use:title class="title">
					{data.title}
					<span />
				</h3>
				<div {...$description(id)} use:description>
					{data.description}
				</div>
				<button {...$close(id)} use:close>
					<Cross />
				</button>
			</div>
		</div>
	{/each}
</div>

<style>
	div.container {
		align-items: flex-end;
		bottom: 0;
		display: flex;
		flex-direction: column;
		gap: 0.5rem;
		margin: 1rem;
		position: fixed;
		right: 0;
		top: auto;
		z-index: 50;
	}

	div.layout {
		border-radius: 0.4rem;
		background-color: var(--surface0);
		color: var(--text);
	}

	div.banner {
		align-items: flex-start;
		display: flex;
		flex-direction: column;
		gap: 1rem;
		padding: 1rem;
		position: relative;
		width: 24rem;
	}

	h3.title {
		display: flex;
		align-items: center;
		gap: 0.4rem;
		font-weight: bold;
	}

	span {
		width: 0.4rem;
		height: 0.4rem;
		background-color: var(--blue);
		border-radius: 999px;
	}

	button {
		width: 1.5rem;
		height: 1.5rem;
		position: absolute;
		right: 1rem;
		top: 1rem;
		display: grid;
		place-items: center;
		border-radius: 999px;
		border: none;
	}

	button:hover {
		background-color: var(--surface1);
	}
</style>
