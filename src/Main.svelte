<script>
    import Button from './Button.svelte';
    import InputCoin from './InputCoin.svelte';
    import Spinner from './Spinner.svelte';
    import { onMount } from 'svelte';
    import { fade } from 'svelte/transition';

    let ready = false;
    let visible = true;

    let locked1 = true;
    let locked2 = true;
    let input1 = "";
    let input2 = "";
    let value1 = 0;
    let value2 = 0;

    var link = 'https://economia.awesomeapi.com.br/last/';

    const table = [
        'BRL',
        'CAD',
        'EUR',
        'JPY',
        'BTC',
        'ETH',
        'USD',
    ]

    const tableDollar = {
        'BRL':.0,
        'CAD':.0,
        'EUR':.0,
        'JPY':.0,
        'BTC':.0,
        'ETH':.0,
    }


    let data = {};
    onMount( async () => {
            //Create the Value of coins
            for ( var coin of table){
                if (coin !== 'USD'){
                    var operation = coin+'-USD';
                    const response = await fetch(link+operation);
                    const result =  await response.json()

                    data[operation] = parseFloat( result[coin+'USD'].high );
                    //Create Value USD to other Coin
                    data['USD-'+coin] = 1 / data[operation];
                    tableDollar[coin] = 1 / data[operation];

                }

            }

            //Use Dollar as Parameter to calculate the value with other coins
            for ( var _coin1 of table){

                if (_coin1 !== 'USD'){

                    for ( var _coin2 of table){

                        if  (_coin2 !== 'USD'){

                            if (_coin1 !== _coin2){
                                data[_coin1+'-'+_coin2] = (data[_coin1+'-USD'] * tableDollar[_coin2] ) ;
                            }

                        }

                    }

                }

            }
            
            ready = true;

    });

    function dataChange1(e){
        input1 = e.detail.coin.value;
        locked1 = false;
        calc1()
    }

    function dataChange2(e){
        input2 = e.detail.coin.value;
        locked2 = false;
        calc2()
    }

    function calc1(){
        const newValue = data[input1+'-'+input2] * value1;
        const step = ( input1 == 'BTC' || input2 == 'BTC' || input1 == 'ETH' || input2 == 'ETH') ? 8 : 4;
        value2 = parseFloat( ( newValue  ).toFixed(step) );
    }

    function calc2(){
        const newValue = data[input2+'-'+input1] * value2;
        const step = ( input1 == 'BTC' || input2 == 'BTC' || input1 == 'ETH' || input2 == 'ETH') ? 8 : 4;
        value1 = parseFloat( ( newValue ).toFixed(step) );
    }

</script>

<div class="box">
    <h1>CLEAN CURRENCY EXCHANGE</h1>
    <hr>
    {#if ready}
        <div id="row">
            <Button on:changeCoin={dataChange1} bind:visible={visible}></Button>
            <Button on:changeCoin={dataChange2} bind:visible={visible}></Button>
        </div>
            <div class='container'>
                {#if visible}
                    <div transition:fade>
                        <InputCoin bind:value={value1} disable={locked1} on:changeValue={calc1}></InputCoin>
                        <InputCoin bind:value={value2} disable={locked2} on:changeValue={calc2}></InputCoin>
                    </div>
                {/if}
            </div>
    {:else}
        <Spinner></Spinner>
    {/if}
</div>

<style>
    .box{
        margin-top: auto;
        margin-left: auto;
        margin-right: auto;
        margin-bottom: 17%;
        height: 225px; 
        width: 70%;
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

    .container{
        min-height: 90.781px;
    }

    #row{
        display: flex;
    }

</style>