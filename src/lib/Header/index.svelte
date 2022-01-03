<script lang="ts">
	import { page } from '$app/stores';
	import { Divider, Menu, Omni, Text } from '@kahi-ui/framework';
</script>

<Omni.Container palette="dark" margin_bottom="large">
	<Omni.Header>
		Kahi UI
		<Divider orientation="vertical" />
		<Text is="small">DEMO</Text>
	</Omni.Header>

	<Omni.Footer>
		<Menu.Container orientation="horizontal">
			<Menu.Anchor href="/" active={$page.path === '/'}>Home</Menu.Anchor>
			<Menu.Anchor href="/about" active={$page.path === '/about'}>About</Menu.Anchor>
			<Menu.Anchor href="/todos" active={$page.path === '/todos'}>Todos</Menu.Anchor>
		</Menu.Container>
	</Omni.Footer>
</Omni.Container>
