<script>
	import { onMount } from "svelte";
	import Joke from "./Joke.svelte";
	async function programmingJokes() {
		const jokes = await fetch(
			"https://official-joke-api.appspot.com/jokes/ten"
		);
		return await jokes.json();
	}
	let promise = programmingJokes();
</script>

<style>
</style>

<div class="container mx-auto px-4 py-6 sm:px-6 lg:px-8">
	<header>
		<div class="max-w-7xl mx-auto bg-white rounded text-gray-700 py-6 px-4 sm:px-6 lg:px-8">
			<h1 class="text-3xl font-bold leading-tight">
				Programming Jokes
			</h1>
		</div>
	</header>
	<main>
		<div class="max-w-7xl mx-auto py-6 px-5 sm:px-6 lg:px-8">
			<div class="grid grid-cols-2 grid-rows-5 gap-4">
				{#await promise}
					<p>...loading</p>
				{:then jokes}
					{#each jokes as joke}
						<Joke {joke} />
					{/each}
					<Joke />
				{/await}
			</div>
		</div>
	</main>
</div>
