<script context="module" lang="ts">
	export const prerender = true;
</script>

<script lang="ts">
	import { Container, Heading, Spacer, Stack } from '@kahi-ui/framework';

	import Counter from '$lib/Counter/index.svelte';
</script>

<svelte:head>
	<title>Home</title>
</svelte:head>

<Stack alignment_x="center">
	<img src="svelte-welcome.png" alt="Welcome" />
</Stack>

<Container>
	<Stack alignment_x="center">
		<Heading>
			to your new
			<br />
			SvelteKit app
		</Heading>

		<Spacer spacing="huge" />

		<Heading is="h2">
			try editing <strong>src/routes/index.svelte</strong>
		</Heading>

		<Spacer spacing="medium" />

		<Counter />
	</Stack>
</Container>
