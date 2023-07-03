<script>
	import Todo from './components/Todo.svelte';
	import AddTask from './components/AddTask.svelte';
	import Warning from './components/Warning.svelte';

	let setTasks = 6;
	let message = '';
	let tasksAdded = 0;

	const addTodo = (e) => {
		let todo = e.detail;

		if(todo.category === '' && todo.task === ''){
			message = "Nothing to add here!";
		}else if(tasksAdded >= setTasks){
			message = "Let's finish up a task on board!"
		}else{
			tasksAdded++;
		} 

		setTimeout(() => {
			message = '';
		}, 2000);
	}

	const removeTodo = () => {
		tasksAdded -= 1;
	}

</script>

<main>
	<div class="wrapper">
		<h2>Stricties!!</h2>
		<p>Let's prioritize and finish!</p>
		<div class="task-form">
			<AddTask {setTasks} on:addTodo={addTodo}/>
		</div>
		<div class="notes">
			<Todo on:removeTodo={removeTodo}/>
		</div>
		{#if message.length>0}
			<Warning message={message} />
		{/if}
	</div>
</main>


<style>
	.wrapper{
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		grid-template-rows: repeat(12, mimax(40px, auto));
	}
	h2{
		color: #d50404;
		grid-column: 1 / 5;
		grid-row: 1 / 2;
		align-self: center;
		justify-self: center;
		font-size: 18px;
		margin-bottom: 5px;
		padding: 0;
	}
	p{
		grid-column: 1 / 5;
		grid-row: 2 / 3;
		align-self: center;
		justify-self: center;
		font-size: 16px;
		padding: 0;
		margin-bottom: 15px;
	}

	.task-form{
		grid-column: 1 / 5;
		grid-row: 3 / 6;
		align-self: center;
		justify-self: center;
	}
	.notes{
		grid-column: 1 / 5;
		grid-row: 6 / 13;
		display: grid;
		grid-template-columns: repeat(1, 1fr);
		grid-template-rows: repeat(6, minmax(150px, auto));
		grid-gap: 5px;
	}
	@media screen and (min-width: 540px){
		.wrapper{
			grid-template-columns: repeat(10, 1fr);
			grid-template-rows: repeat(12, mimax(60px, auto));
		}
		h2{
			grid-column: 1 / 11;
			grid-row: 1 / 2;
			align-self: center;
			justify-self: center;
		}
		p{
			grid-column: 1 / 11;
			grid-row: 2 / 3;
			align-self: center;
			justify-self: center;
		}

		.task-form{
			grid-column: 1 / 11;
			grid-row: 3 / 6;
			align-self: center;
			justify-self: center;
		}
		.notes{
			grid-column: 1 / 11;
			grid-row: 6 / 13;
			display: grid;
			grid-template-columns: repeat(3, 1fr);
			grid-template-rows: repeat(2, minmax(250px, auto));
			grid-gap: 5px;
		}
	}

	@media screen and (min-width: 768px){
		.wrapper{
			grid-template-columns: repeat(15, 1fr);
			grid-template-rows: repeat(15, mimax(60px, auto));
		}
		h2{
			grid-column: 1 / 16;
			grid-row: 1 / 2;
			align-self: center;
			justify-self: center;
			font-size: 20px;
		}
		p{
			grid-column: 1 / 16;
			grid-row: 2 / 3;
			align-self: center;
			justify-self: center;
			font-size: 18px;
		}

		.task-form{
			grid-column: 1 / 16;
			grid-row: 3 / 6;
			align-self: center;
			justify-self: center;
		}
		.notes{
			grid-column: 1 / 16;
			grid-row: 6 / 16;
			display: grid;
			grid-template-columns: repeat(3, 1fr);
			grid-template-rows: repeat(2, minmax(300px, auto));
			grid-gap: 5px;
		}
	}

	@media screen and (min-width: 1024px){
		.wrapper{
			grid-template-columns: repeat(12, 1fr);	
			grid-template-rows: repeat(12, minmax(50px, auto));
			text-align: center;
		}

		h2{
			grid-column: 1 / 13;
			grid-row: 1 / 2;
			align-self: center;
			justify-self: center;
			font-size: 22px;
		}

		p{
			grid-column: 1 / 13;
			grid-row: 2 / 3;
			align-self: center;
			justify-self: center;
			font-size: 20px;
		}

		.task-form{
			grid-column: 1 / 5;
			grid-row: 1 / 13;
			align-self: center;
			justify-self: center;
		}
		.notes{
			grid-column: 5 / 13;
			grid-row: 3 / 13;
			display: grid;
			grid-template-columns: repeat(3, 1fr);
			grid-template-rows: repeat(2, minmax(250px, auto));
			grid-gap: 5px;
		}

	}
	
</style>