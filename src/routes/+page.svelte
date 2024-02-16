<script>
	import Button from '$lib/components/Button.svelte';
	import Label from '$lib/components/Label.svelte';
	import Select from '$lib/components/Select.svelte';
	import Switch from '$lib/components/Switch.svelte';
</script>


<section>
	<h2>Button</h2>
	<div><Button /></div>
</section>

<section>
	<h2>Label</h2>
	<div><Label /></div>
</section>

<section>
	<h2>Select</h2>
	<div><Select /></div>
</section>

<section>
	<h2>Switch</h2>
	<div><Switch /></div>
</section>

<style>
	section {
		align-items: center;
		background-color: var(--mantle);
		border: thin solid var(--crust);
		border-radius: 16px;
		display: flex;
		gap: 0.4rem;
		justify-content: center;
	}

	section h2 {
		align-self: flex-start;
		background-color: var(--crust);
		border-radius: 16px 16px 0 0;
		color: var(--text);
		font-size: 1.2rem;
		margin: 0;
		padding: 0.8rem 1.2rem;
		width: 100%;
	}

	section div {
		padding: 2rem 0;
	}
</style>
