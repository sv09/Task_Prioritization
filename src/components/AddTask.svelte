<script>
    import { createEventDispatcher } from "svelte";
    import Button from "./reusable/button.svelte";
    import { TodoStore } from "../store";

    export let setTasks;

    let todo={};
    let category = '';
    let task ='';
    let uid = 1;

    let dispatch = createEventDispatcher();

    const handleSubmit = () => {
        todo = {
            category,
            task,
            id: uid++
        }
        category = '';
        task = '';

        // console.log('store length - ', $TodoStore.length)
        if($TodoStore.length < setTasks){
            if(todo.category != '' || todo.task != ''){
            TodoStore.update(data => {
                return [...data, todo];
            });
        }
        }
        dispatch('addTodo', todo);
	}
</script>

<form on:submit|preventDefault={handleSubmit}> 
    <input type="text" placeholder="Category" bind:value={category} id="category"/>
    <input type="text" placeholder="What is to be done?" bind:value={task} id="task"/>
    <div class="add-task">
        <Button>+</Button>
    </div>
</form>


<style>
    input{
        display: block;
        border-radius: 15px;
        padding: 0.3rem;
        font-size: 12px;
    }
    #category{
        width: 12rem;
        text-align: center;
    }
    #task{
        width: 12rem;
        text-align: center;
    }
    .add-task{
        text-align: center;
    }
    @media screen and (min-width: 540px){
        input{
            padding: 0.4rem;
            font-size: 14px;
        }
        #category{
            width: 20rem;
            text-align: center;
        }
        #task{
            width: 20rem;
            text-align: center;
        }
    }
    @media screen and (min-width: 768px){
        input{
            padding: 0.6rem;
        }
        #category{
            width: 20rem;
            text-align: center;
        }
        #task{
            width: 20rem;
            text-align: center;
        }
        .add-task{
            text-align: center;
        }
    }
    @media screen and (min-width: 1024px){
        input{
            padding: 0.6rem;
        }
        #category{
            width: 20rem;
            text-align: center;
        }
        #task{
            width: 20rem;
            text-align: center;
        }
    }

</style>