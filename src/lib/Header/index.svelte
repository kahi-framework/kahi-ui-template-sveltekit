<script lang="ts">
	import { page } from '$app/stores';
	import { Box, Divider, Menu, Omni, Popover, Text } from '@kahi-ui/framework';
</script>

<Omni.Container palette="dark" margin_bottom="large">
	<Omni.Header>
		Kahi UI
		<Divider orientation="vertical" />
		<Text is="small">DEMO</Text>
	</Omni.Header>

	<Omni.Footer>
		<Menu.Container orientation="horizontal" hidden="mobile">
			<Menu.Anchor href="/" active={$page.url.pathname === '/'}>Home</Menu.Anchor>
			<Menu.Anchor href="/about" active={$page.url.pathname === '/about'}>About</Menu.Anchor>
			<Menu.Anchor href="/todos" active={$page.url.pathname === '/todos'}>Todos</Menu.Anchor>
		</Menu.Container>

		<Popover.Container
			logic_id="header-popover"
			hidden={['tablet', 'desktop', 'widescreen']}
			dismissible
		>
			<Popover.Button variation="clear">+</Popover.Button>

			<Popover.Section alignment_x="left" spacing="small">
				<Box palette="auto" elevation="high" padding="medium" shape="rounded">
					<Menu.Container>
						<Menu.Anchor href="/" active={$page.url.pathname === '/'}>Home</Menu.Anchor>
						<Menu.Anchor href="/about" active={$page.url.pathname === '/about'}>About</Menu.Anchor>
						<Menu.Anchor href="/todos" active={$page.url.pathname === '/todos'}>Todos</Menu.Anchor>
					</Menu.Container>
				</Box>
			</Popover.Section>
		</Popover.Container>
	</Omni.Footer>
</Omni.Container>
