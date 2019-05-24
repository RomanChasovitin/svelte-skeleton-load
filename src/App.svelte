<script>
	import SkeletonLoader from './components/SkeletonLoader.svelte'
	export let name;
	let todos = getTodos();
	let skeleton = new Array();
	skeleton.length = 100;

	async function getTodos() {
		let res = await fetch('https://jsonplaceholder.typicode.com/todos')
		res = await res.json();
		if(res){
			return res;
		} else {
			throw new Error('Error with load')
		}
	}

	function randomWidth() {
		const rand = Math.floor(Math.random() * (100 - 20)) + 20;
		return `${rand}%`;
	}
</script>

<style>
	.wrapper{
		margin: 20px auto;
		width: 970px;
	}
	.todo {
		font-family: sans-serif;
		margin-bottom: 8px;
		font-size: 16px;
		line-height: 1;
		font-weight: bold;
	}
</style>

<SkeletonLoader
	type="string"
	animated={true}
	count={1}
	fontSize='16px'
	width={'100%'}
/>

<div class="wrapper">
	{#await todos}
		{#each skeleton as skelet }
			<SkeletonLoader
				type="string"
				animated={true}
				count={1}
				fontSize='16px'
				width={randomWidth()}
			/>
		{/each}
	{:then todos}
		{#each todos as todo }
			<div class="todo">#{todo.id} {todo.title}</div>
		{/each}
	{:catch }
		error :(
	{/await}
</div>