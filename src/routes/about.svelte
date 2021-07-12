<script context="module">
	import { browser, dev } from '$app/env';
	import { Code, Container, Heading, Text } from '@kahi-ui/framework';

	// we don't need any JS on this page, though we'll load
	// it in dev so that we get hot module replacement...
	export const hydrate = dev;

	// ...but if the client-side router is already loaded
	// (i.e. we came here from elsewhere in the app), use it
	export const router = browser;

	// since there's no dynamic data here, we can prerender
	// it so that it gets served as a static asset in prod
	export const prerender = true;
</script>

<svelte:head>
	<title>About</title>
</svelte:head>

<Container>
	<Heading margin_bottom="medium">About this app</Heading>

	<Text>
		This is a <a href="https://kit.svelte.dev">SvelteKit</a> app. You can make your own by typing the
		following into your command line and following the prompts:
	</Text>

	<!-- TODO lose the @next! -->
	<Code is="pre" margin_y="medium">npm init svelte@next</Code>

	<Text margin_bottom="small">
		The page you're looking at is purely static HTML, with no client-side interactivity needed.
		Because of that, we don't need to load any JavaScript. Try viewing the page's source, or opening
		the devtools network panel and reloading.
	</Text>

	<Text>
		The <a href="/todos">TODOs</a> page illustrates SvelteKit's data loading and form handling. Try using
		it with JavaScript disabled!
	</Text>
</Container>
