<script lang="ts">
	import Github from '$lib/icons/Github.svelte';
	import Layers from './icons/Layers.svelte';
</script>

<header>
	<a href="/" class="name"><Layers />astro<span>lib</span></a>
	<span class="line"></span>
	<a href="https://github.com/lewinkoon" class="link"><Github /></a>
</header>

<style>
	header {
		display: flex;
		align-items: baseline;
		gap: 1rem;
		max-width: 1080px;
		width: 100%;
		margin-bottom: 2rem;
	}

	a.name {
		display: flex;
		font-size: 1.6rem;
	}

	a.name span {
		color: var(--lavender);
		transition: color 0.2s ease-in-out;
	}

	a.name:hover span {
		color: var(--red);
	}

	span.line {
		flex-grow: 1;
		border-bottom: 2px solid var(--surface0);
		border-radius: 1px;
		margin: auto 0;
	}

	a.link {
		display: flex;
		place-items: center;
		padding: 0.5rem;
		border-radius: 8px;
		transition: background-color 0.2s ease-in-out;
	}

	a.link:hover {
		background-color: var(--surface0);
	}
</style>
