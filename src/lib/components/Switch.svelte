<script lang="ts">
	import { createSwitch } from '@melt-ui/svelte';
	import { theme } from '$lib/stores';
	const {
		elements: { root, input }
	} = createSwitch({
		defaultChecked: state()
	});

	function toggle() {
		if ($theme == 'dark') {
			$theme = 'light';
		} else if ($theme == 'light') {
			$theme = 'dark';
		} else {
			$theme = 'light';
		}
	}

	function state() {
		if ($theme == 'dark') {
			return true
		} else if ($theme == 'light') {
			return true
		} else {
			return false
		}
	}
</script>

<form>
	<div class="container">
		<label for="airplane-mode" id="airplane-mode-label"> Airplane mode </label>
		<button
			on:click={toggle}
			{...$root}
			use:root
			id="airplane-mode"
			aria-labelledby="airplane-mode-label"
		>
			<span />
		</button>
		<input {...$input} use:input />
	</div>
</form>

<style>
	div.container {
		display: flex;
		align-items: center;
	}

	label {
		padding-right: 1rem;
		line-height: 1;
	}

	button {
		position: relative;
		height: 1.5rem;
		cursor: default;
		border-radius: 999px;
		background-color: var(--surface1);
		transition-property: color, background-color, border-color, text-decoration-color, fill, stroke;
		transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
		transition-duration: 0.15s;
		width: 2.75rem;
	}

	button[data-state='checked'] {
		background-color: var(--surface0);
	}

	span {
		display: block;
		background-color: var(--lavender);
		border-radius: 999px;
		width: 1.25rem;
		height: 1.25rem;
		transform: translate(-0.125rem);
		transition-property:
			color,
			background-color,
			border-color,
			text-decoration-color,
			fill,
			stroke,
			opacity,
			box-shadow,
			transform,
			filter,
			backdrop-filter,
			-webkit-backdrop-filter;
		transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
		transition-duration: 0.15s;
	}

	:global([data-state='checked']) span {
		transform: translateX(calc(2.75rem - 1.5rem - 0.125rem));
	}
</style>
