<script>
	import {slide} from 'svelte/transition';
	import {elasticInOut} from 'svelte/easing';
	import { text } from 'svelte/internal';

	let todos = [];
	let input = '';

	function addTodo () {
		if(input)
		todos = [
			...todos,
			{
				text: input,
				id: Math.random().toString(36).substr(2, 9)
			}
		];
		input = '';
	}
	function removeTodo(id) {
		const index = todos.findIndex(todo => todo.id === id);
		todos.splice(index, 1);
		todos = todos;
	}

	function alertnya() {
	}
</script>

<style></style>

<svelte:head>
	<link href="https://unpkg.com/tailwindcss@^2/dist/tailwind.min.css" rel="stylesheet">
	<script src="https://use.fontawesome.com/releases/v5.3.1/js/all.js"></script>
</svelte:head>

<main class="flex flex-col">
	<h4 class="text-2xl text-center">Svelte Todo + Tailwind</h4>
	 <div class="mt-10 flex flex-col">
		<form class="flex justify-center" action="" on:submit|preventDefault={addTodo}>
			<input type="text" bind:value={input} placeholder="Add your todo...">
			<button class ="bg-black w-10 h-10">
				<i class="fas fa-plus text-white"></i>
			</button>
		</form>
		<ul class:list={todos.length > 0} class="flex justify-center mt-20">
		{#each todos as todo (todo.id)}
			<li transition:slide="{{duration: 300, easing: elasticInOut}}">
				<span>{todo.text}</span>
				<button class ="w-10 h-auto" on:click={() => removeTodo(todo.id)}>
					<i class="fas fa-trash"></i>
				</button>
			</li>
		{:else}
			<div class="header flex flex-col">
			<li class="flex">Nothing Else</li>
			<a href="https://github.com/floxydio/" target="_blank"><i class="fab fa-github mt-10 text 2xl"></i></a>
		</div>
		{/each}
	</ul> 
</main>