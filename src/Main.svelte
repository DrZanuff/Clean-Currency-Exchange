<script>
    import Button from './Button.svelte';
</script>

<div class="box">
    <h1>CLEAN CURRENCY EXCHANGE</h1>
    <hr>
    <div>
        <Button></Button>
    </div>
</div>

<style>
    .box{
/*         margin-left: auto;
        margin-right: auto; */
        margin: auto;
        height: 225px; 
        width: 50%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-content: center;
        align-items: center;
    }

    h1{
        color: white;
        font-size: 24px;
        line-height: 39px;
        text-align: center;
        font-family: Sarala;
        font-style: normal;
        font-weight: normal;
        font-size: 24px;
    }

    hr{
        width: 70%;
        border-top: 1px;
        opacity: .5;
    }

</style>