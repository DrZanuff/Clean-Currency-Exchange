<script>
    export let value = 0;
    export let disable = true;

    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();

    function handle(){
        dispatch( 'changeValue' , { 'value' : value } )
    }
</script>

<input type="number" bind:value={value} disabled={disable} on:input={handle}>

<style>
    input{
        border: 2px solid rgba(255, 255, 255, 0.44);
        background-color: #ffffff00;
        box-sizing: border-box;
        border-radius: 2px;
        max-width: 200px;
        min-height: 42px;
        margin-left: 25px;
        margin-right: 25px;
        margin-top: 40px;
        outline: none;
        font-family: Sarala;
        color: white;
/*         text-align: center; */
    }
</style>