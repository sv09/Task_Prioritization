<script>
    import Button from "./reusable/button.svelte";
    import { createEventDispatcher } from "svelte";
    import { flip } from 'svelte/animate';
    import { scale, fade } from "svelte/transition";
    import { TodoStore } from "../store";
    // export let tasks;

    let dispatch = createEventDispatcher();
    const removeTask = (todo) => {
        dispatch('removeTodo');
        TodoStore.update(data => {
            return data.filter(d => d.id != todo.id);
        });
    }

</script>

{#if $TodoStore.length > 0}
    {#each $TodoStore as todo (todo.id)}
        <div class="sticky" animate:flip={{ duration: 500}} in:fade out:scale>
            <h3 class="header">{todo.category}</h3>
            <p class="note">{todo.task}</p>
            <div class="remove">
                <Button on:click={() => removeTask(todo)}>-</Button>
            </div>
        </div>
    {/each}
{/if}


<style>
    .sticky{
        border: 1px solid gray;
        text-align: center;
        font-family: Arial, Helvetica, sans-serif;
        color: #444;
        background: rgba(238, 224, 67, 0.45);
        align-self: center;
        justify-self: center;
        width: 120px;
        height: 140px;
    }
    .sticky .header{
        border: 1px solid #f1e34b;
        padding: 0.75rem;
        max-width: 100%;
        background: rgba(238, 224, 67, 0.3);
        margin: 0;
        height: 8px;
        font-size: 14px;
    }
    .sticky .note{
        font-size: 14px;
    }
    .remove{
        margin-top: 3rem;
    }
    @media screen and (min-width: 540px){
        .sticky{
            width: 150px;
            height: 220px;
        }
        .sticky .header{
            height: 12px;
            font-size: 17px;
        }
        .sticky .note{
            font-size: 18px;
            padding: 1rem;
            min-width: 80px;
            font-size: 16px;
        }
        .remove{
            margin-top: 4rem;
        }
    }
    @media screen and (min-width: 768px){
        .sticky{
            width: 200px;
            height: 250px;
        }
        .sticky .header{
            height: 15px;
        }
        .sticky .note{
            font-size: 18px;
            padding: 1rem;
            min-width: 80px;
        }
        .remove{
            margin-top: 5rem;
        }
    }

    @media screen and (min-width: 1024px){
        .sticky{
            width: 200px;
            height: 250px;
        }
        .sticky .header{
            height: 15px;
        }
        .sticky .note{
            font-size: 18px;
            padding: 1rem;
            min-width: 80px;
        }
        .remove{
            margin-top: 5rem;
        }
    }


</style>