<script>
    import { fade } from "svelte/transition";

    export let message;

</script>

<div class= "warning" id="warning">
    <p transition:fade>{ message }</p>
</div>

<style>
    .warning{
        text-align: center;
        color: #555;
        background-color: rgba(212, 212, 212, 0.6);
        border-radius: 30px;
        padding: 1rem;
        grid-column: 2 / 4;
        grid-row: 7 / 9;
        font-size: 12px;
    }
    @media screen and (min-width: 540px){
        .warning{
            grid-column: 3 / 9;
            grid-row: 7 / 9;
            font-size: 14px;
        }
    }
    @media screen and (min-width: 768px){
        .warning{
            grid-column: 5 / 12;
            grid-row: 8 / 11;
            font-size: 16px;
            padding: 3rem;
        }
    }
    @media screen and (min-width: 1024px){
        .warning{
            grid-column: 5 / 9;
            grid-row: 6 / 9;
            font-size: 16px;
            padding: 3rem;
        }
    }

</style>