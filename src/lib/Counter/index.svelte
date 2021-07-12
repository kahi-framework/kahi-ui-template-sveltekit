<script lang="ts">
	import { Button, Stack, Text } from '@kahi-ui/framework';

	let count = 0;
</script>

<Stack orientation="horizontal" alignment_y="center" spacing="large">
	<Button palette="negative" size="large" on:click={() => (count -= 1)}>-</Button>

	<Text is="strong" size="huge">{count}</Text>

	<Button palette="affirmative" size="large" on:click={() => (count += 1)}>+</Button>
</Stack>
