<script>
</script>

<button class="button" on:click>
    <slot></slot>
</button>

<style>
    .button{
        width: 1.3em;
		height: 1.3em;
        border-radius: 15px;
        text-align: center;
        background-color: rgba(212, 212, 212, 0.4);
        padding: 0;
    }

    @media screen and (min-width: 540px){
        .button{
            width: 1.5rem;
            height: 1.5rem;
        }
    }
    @media screen and (min-width: 768px){
        .button{
            width: 2em;
		    height: 2em;
        }
    }

</style>