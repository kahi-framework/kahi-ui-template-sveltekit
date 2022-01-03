<script lang="ts">
	import '@kahi-ui/framework/dist/kahi-ui.framework.css';
	import { Anchor, Box, Spacer, Text } from '@kahi-ui/framework';

	import Header from '$lib/Header/index.svelte';
</script>

<Header />

<main>
	<slot />
</main>

<Spacer />

<Box margin_top="large" padding_x="medium" padding_y="huge">
	<Text align="center">
		visit <Anchor href="https://kit.svelte.dev" palette="accent">kit.svelte.dev</Anchor> to learn SvelteKit
		<br />
		visit <Anchor href="https://kahi-ui.nbn.dev" palette="accent">kahi-ui.nbn.dev</Anchor> to learn Kahi
		UI
	</Text>
</Box>

<style>
	:global(#svelte) {
		display: flex;
		flex-direction: column;

		min-height: 100vh;
	}
</style>
