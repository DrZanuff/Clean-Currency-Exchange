<style>
    .select{
        --background : #ffffff00;
        --border: 2px solid #fff;
        --borderRadius: 2px;
        color: white;
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
</script>

<div class="select">
    <Select {items} {selectedValue}></Select>
</div>
