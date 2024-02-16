<script lang="ts">
	import Header from '$lib/Header.svelte';
	import Footer from '$lib/Footer.svelte';
	import Toast from '$lib/components/Toast.svelte';
	import { theme } from '$lib/stores';
</script>

<svelte:head>
	<meta name="color-scheme" content={$theme == 'system' ? 'light dark' : $theme} />
	<link rel="stylesheet" href={`/${$theme}.css`} />
	<title>Playground</title>
</svelte:head>

<Header />

<Toast />

<slot />

<Footer />

<style>
	:root {
		font-family: regular;
		font-size: 12pt;
		color: var(--text);
		scrollbar-gutter: stable both-edges;
		scroll-behavior: smooth;
		background-color: var(--base);
	}

	@font-face {
		font-family: regular;
		src: url(/Inter.ttf) format('truetype');
	}

	:global(*) {
		box-sizing: border-box;
		border-width: 0;
		border-style: solid;
		border-color: var(--blue);
	}

	:global(body) {
		display: flex;
		flex-direction: column;
		align-items: center;
		padding: 2rem;
		margin: 0;
	}

	:global(section) {
		display: flex;
		flex-direction: column;
		max-width: 800px;
		width: 100%;
		margin-bottom: 2rem;
	}

	:global(h1, h2, h3, h4, h5, h6) {
		font-weight: normal;
		margin: 0;
	}

	:global(p, ol, ul, dl, table, blockquote) {
		font-size: 1.2rem;
		margin: 0 0 1.5rem;
		color: var(--text);
	}

	:global(button, input, select) {
		color: inherit;
		font-family: inherit;
		font-size: inherit;
		font-weight: inherit;
		margin: 0;
		background: transparent;
	}

	:global(a) {
		text-decoration: none;
		color: var(--text);
	}

	:global(em) {
		color: var(--green);
		font-style: italic;
	}
</style>
