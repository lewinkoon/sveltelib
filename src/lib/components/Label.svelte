<script lang="ts">
	import { createLabel, melt } from '@melt-ui/svelte';

	const {
		elements: { root }
	} = createLabel();
</script>

<form>
	<label {...$root} use:root for="email" data-melt-part="root">
		<span>Email</span>
	</label>
	<input type="text" id="email" placeholder="vanilla@melt-ui.com" />
</form>

<style>
	form {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: start;
	}

	label {
		margin-bottom: 0.5rem;
	}

	input {
		background-color: var(--surface0);
		border: thin solid var(--surface1);
		border-radius: 8px;
		padding: 0.8rem 1.2rem;
		outline: none;
	}
</style>
