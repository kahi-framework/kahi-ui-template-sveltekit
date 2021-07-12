<script context="module" lang="ts">
	import { enhance } from '$lib/form';
	import type { Load } from '@sveltejs/kit';

	// see https://kit.svelte.dev/docs#loading
	export const load: Load = async ({ fetch }) => {
		const res = await fetch('/todos.json');

		if (res.ok) {
			const todos = await res.json();

			return {
				props: { todos }
			};
		}

		const { message } = await res.json();

		return {
			error: new Error(message)
		};
	};
</script>

<script lang="ts">
	import { Button, Container, Heading, Spacer, Stack, TextInput, Tile } from '@kahi-ui/framework';

	type Todo = {
		uid: string;
		created_at: Date;
		text: string;
		done: boolean;
	};

	export let todos: Todo[];

	async function patch(res: Response) {
		const todo = await res.json();

		todos = todos.map((t) => {
			if (t.uid === todo.uid) return todo;
			return t;
		});
	}

	function on_text_blur(text: string, event: FocusEvent) {
		const target = event.target as HTMLInputElement;

		// NOTE: Instead of just resetting the title on input blur, we could
		// just instead submit here.
		if (target.value !== text) target.value = text;
	}
</script>

<svelte:head>
	<title>Todos</title>
</svelte:head>

<Container>
	<Heading margin_bottom="medium">Todos</Heading>

	<form
		class="new"
		action="/todos.json"
		method="post"
		use:enhance={{
			result: async (res, form) => {
				const created = await res.json();
				todos = [...todos, created];

				form.reset();
			}
		}}
	>
		<TextInput name="text" placeholder="+ tap to add a todo" variation="block" />
	</form>

	<Spacer spacing="large" />

	<Stack spacing="medium">
		{#each todos as todo (todo.uid)}
			<Tile.Container palette={todo.done ? 'accent' : undefined}>
				<Tile.Section>
					<Tile.Header>
						<form
							class="text"
							action="/todos/{todo.uid}.json?_method=patch"
							method="post"
							use:enhance={{
								result: patch
							}}
						>
							<TextInput
								name="text"
								value={todo.text}
								variation="flush"
								on:blur={(event) => on_text_blur(todo.text, event)}
							/>
						</form>
					</Tile.Header>
				</Tile.Section>

				<Tile.Footer>
					<form
						action="/todos/{todo.uid}.json?_method=patch"
						method="post"
						use:enhance={{
							pending: (data) => {
								todo.done = !!data.get('done');
							},
							result: patch
						}}
					>
						<input type="hidden" name="done" value={todo.done ? '' : 'true'} />

						<Button palette={todo.done ? 'negative' : 'affirmative'}>
							{@html todo.done ? '&cross;' : '&check;'}
						</Button>
					</form>

					<form
						action="/todos/{todo.uid}.json?_method=delete"
						method="post"
						use:enhance={{
							result: () => {
								todos = todos.filter((t) => t.uid !== todo.uid);
							}
						}}
					>
						<Button palette="negative">-</Button>
					</form>
				</Tile.Footer>
			</Tile.Container>
		{/each}
	</Stack>
</Container>
