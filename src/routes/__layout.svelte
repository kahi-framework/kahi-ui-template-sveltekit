<script lang="ts">
	import '@kahi-ui/framework/dist/kahi-ui.framework.css';
	import { Box, Spacer, Text } from '@kahi-ui/framework';

	import Header from '$lib/Header/index.svelte';
</script>

<Header />

<main>
	<slot />
</main>

<Spacer />

<Box margin_top="large" padding_x="medium" padding_y="huge">
	<Text align="center">
		visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to learn SvelteKit
		<br />
		visit <a href="https://kahi-ui.nbn.dev">kahi-ui.nbn.dev</a> to learn Kahi UI
	</Text>
</Box>

<style>
	:global(#svelte) {
		display: flex;
		flex-direction: column;

		min-height: 100vh;
	}
</style>
