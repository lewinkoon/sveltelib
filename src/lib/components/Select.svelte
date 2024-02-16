<script lang="ts">
	import { createSelect } from '@melt-ui/svelte';
	import { fade } from 'svelte/transition';
	import ChevronDown from '$lib/icons/ChevronDown.svelte';
	import Check from '$lib/icons/Check.svelte';
	import { theme } from '$lib/stores';

	const options = {
		system: 'System',
		light: 'Light',
		dark: 'Dark'
	};

	const {
		elements: { trigger, menu, option, label },
		states: { selected, selectedLabel, open },
		helpers: { isSelected }
	} = createSelect({
		defaultSelected: { value: 'system', label: 'System' },
		forceVisible: true,
		positioning: {
			placement: 'bottom',
			fitViewport: true,
			sameWidth: true
		}
	});

	$: $theme = $selected?.value as string
</script>

<div class="container">
	<!-- svelte-ignore a11y-label-has-associated-control - $label contains the 'for' attribute -->
	<label {...$label} use:label>Chosen theme</label>
	<button class="trigger" {...$trigger} use:trigger aria-label="Food">
		{$selectedLabel || 'Select a flavor'}
		<ChevronDown />
	</button>
	{#if $open}
		<div class="menu" use:menu transition:fade={{ duration: 150 }}>
			{#each Object.entries(options) as [key, item]}
				<div class="option" {...$option({ value: key, label: item })} use:option>
					<div class="check {$isSelected(item) ? 'block' : 'hidden'}">
						<Check />
					</div>
					{item}
				</div>
			{/each}
		</div>
	{/if}
</div>

<style>
	.container {
		display: flex;
		flex-direction: column;
		gap: 1rem;
	}

	label {
		display: block;
	}

	button.trigger {
		align-items: center;
		border: thin solid var(--surface0);
		border-radius: 12px;
		background-color: var(--surface0);
		display: flex;
		justify-content: space-between;
		height: 2.5rem;
		min-width: 220px;
		padding: 0.5rem 0.75rem;
	}

	div.menu {
		background-color: var(--surface0);
		border-radius: 0.5rem;
		display: flex;
		flex-direction: column;
		max-height: 300px;
		overflow-y: auto;
		padding: 0.25rem;
		z-index: 10;
	}

	div.group-label {
		font-weight: bold;
		padding: 0.25rem 0.5rem;
		text-transform: capitalize;
	}

	div.option {
		border-radius: 0.5rem;
		cursor: pointer;
		position: relative;
		padding: 0.25rem 1rem 0.25rem 2rem;
	}

	div.option[data-highlighted] {
		background-color: var(--surface2);
	}

	div.option[data-disabled] {
		opacity: 50%;
	}

	div.option:focus {
		z-index: 10;
	}

	div.option:hover {
		background-color: var(--surface1);
	}

	div.check {
		color: var(--red);
		left: 0.5rem;
		position: absolute;
		top: 50%;
		translate: 0 calc(-50% + 1px);
		z-index: 20;
	}

	div.block {
		display: block;
	}

	div.hidden {
		display: none;
	}
</style>
