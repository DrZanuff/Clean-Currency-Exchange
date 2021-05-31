<script>
    import Button from './Button.svelte';
    import InputCoin from './InputCoin.svelte';
    import { onMount } from 'svelte';

    let input1 = "";
    let input2 = "";

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

            console.log(data);

    });


</script>

<div class="box">
    <h1>CLEAN CURRENCY EXCHANGE</h1>
    <hr>
    <div id="row">
        <Button></Button>
        <Button></Button>
    </div>
    <div>
        <InputCoin></InputCoin>
        <InputCoin></InputCoin>
    </div>
</div>

<style>
    .box{
        margin-top: auto;
        margin-left: auto;
        margin-right: auto;
        margin-bottom: 17%;
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

    #row{
        display: flex;
    }

</style>