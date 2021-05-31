<style>
    .select{
        --background : #ffffff00;
        --border: 2px solid #fff;
        --borderRadius: 2px;
        color: white;
        min-width: 137px;
        font-family: Sarala;
        --listBackground: #04040446;
        --itemColor: #FFFFFF;
        --itemHoverBG: #00000080;
        margin-left: 25px;
        margin-right: 25px;
        margin-top: 40px;
    }

    .select:focus-within{
        --background : #ffffff;
        color: #494949;
        min-width: 137px;
        font-family: Sarala;
        --listBackground: #04040446;
        --itemColor: #FFFFFF;
        --itemHoverBG: #00000080;
        margin-left: 25px;
        margin-right: 25px;
        margin-top: 40px;
    }


</style>

<script>
    import Select from 'svelte-select';

    let items = [
        {value: 'USD', label: 'USD'},
        {value: 'BRL', label: 'BRL'},
        {value: 'CAD', label: 'CAD'},
        {value: 'EUR', label: 'EUR'},
        {value: 'JPY', label: 'JPY'},
        {value: 'BTC', label: 'BTC'},
        {value: 'ETH', label: 'ETH'},
    ];

    let selectedValue = {value: 'none', label: 'Select Coin'};

    function handle(event){
        console.log(event.detail);
    }

</script>

<div class="select">
    <Select {items} {selectedValue} on:select={handle}></Select>
</div>
