<script>
export default {
  el: '#currencies-data',
  data: () => ({

    currencies: [
          {
          "name": "BTC",
          "decimals": 9,
          "description": "Bitcoin",
          "conversion": {
          "btc": 1,
          "usd": 6973.18
          },
          "balance": 0.032
          },
          {
          "name": "ETH",
          "decimals": 6,
          "description": "Ethereum",
          "conversion": {
          "btc": 0.002,
          "usd": 132.19
          },
          "balance": 2.13
          },
          {
          "name": "BUSD",
          "decimals": 2,
          "description": "Binance USD",
          "conversion": {
          "btc": 0.0000082,
          "usd": 19
          },
          "balance": 190
          },
          {
          "name": "ELLO",
          "decimals": 4,
          "description": "Ichello",
          "conversion": {
          "btc": 0.0081,
          "usd": 112
          },
          "balance": 46228.13
          },
          {
          "name": "DASH",
          "decimals": 5,
          "description": "Dash",
          "conversion": {
          "btc": 0.01,
          "usd": 737
          },
          "balance": 3.13
          },
          {
          "name": "GUSD",
          "decimals": 6,
          "description": "Gemini",
          "conversion": {
          "btc": 0.00032,
          "usd": 12
          },
          "balance": 433
          },
          {
          "name": "MIOTA",
          "decimals": 3,
          "description": "IOTA",
          "conversion": {
          "btc": 0.00182,
          "usd": 11
          },
          "balance": 0
          },
          {
          "name": "LTC",
          "decimals": 11,
          "description": "Litecoin",
          "conversion": {
          "btc": 0.22,
          "usd": 1239
          },
          "balance": 322
          },
          {
          "name": "XMR",
          "decimals": 7,
          "description": "Monero",
          "conversion": {
          "btc": 0.03,
          "usd": 180
          },
          "balance": 0
          },
          {
          "name": "NEO",
          "decimals": 9,
          "description": "NEO",
          "conversion": {
          "btc": 0.00086,
          "usd": 3.09
          },
          "balance": 1200
          },
          {
          "name": "PAX",
          "decimals": 8,
          "description": "Paxos",
          "conversion": {
          "btc": 0.00013,
          "usd": 0.34
          },
          "balance": 923
          },
          {
          "name": "XRP",
          "decimals": 5,
          "description": "Ripple",
          "conversion": {
          "btc": 0.34,
          "usd": 932.19
          },
          "balance": 0
          },
          {
          "name": "USDS",
          "decimals": 7,
          "description": "StableUSD",
          "conversion": {
          "btc": 0.000135,
          "usd": 0.04
          },
          "balance": 0
          },
          {
          "name": "XLM",
          "decimals": 5,
          "description": "Stellar",
          "conversion": {
          "btc": 0.0009102,
          "usd": 1.31
          },
          "balance": 830
          },
          {
          "name": "USDT",
          "decimals": 2,
          "description": "Tether",
          "conversion": {
          "btc": 0.089,
          "usd": 932
          },
          "balance": 491.13
          },
          {
          "name": "TRX",
          "decimals": 9,
          "description": "Tron",
          "conversion": {
          "btc": 0.003201,
          "usd": 902
          },
          "balance": 0
          },
          {
          "name": "TUSD",
          "decimals": 2,
          "description": "TrueUSD",
          "conversion": {
          "btc": 0.00328,
          "usd": 1
          },
          "balance": 910
          },
          {
          "name": "ZEC",
          "decimals": 11,
          "description": "Zcash",
          "conversion": {
          "btc": 0.0001803,
          "usd": 0.21
          },
          "balance": 0
          }
          ]
          })
        }

// import axios from 'axios'

// export default {
//   data () {
//     return {
//       currencies: []
//     }
//   },
//   async mounted () {
//     await axios.get('https://ichello.nyc3.digitaloceanspaces.com/test/currencies.json')
//     .then(res => console.log(res))
//   }
// }

</script>
<template>
  <div class="container">
    <p>Teste Técnico Ichello</p>
    <p>Passe o mouse abaixo para ver o Saldo Total em USD</p>
    <p></p>
    <figure class="card" style="--bg-image-url: url();">
      <img class="card__image" alt="" src="https://www.onze.com.br/blog/wp-content/uploads/2020/08/shutterstock_382756228-770x478.jpg">
      <p class="card__info">US$ {{ currencies.map(currencie => currencie.balance * currencie.conversion.usd).reduce((prev, curr) => prev + curr, 0) }}</p>
    </figure>
    <p>Tabela de Moedas</p>
    <table class="table-scroll small-first-col" >  
      <tbody class="body-half-screen">
        <tr v-for="currencie in currencies">
          <td v-if="currencie.balance > 0">{{ currencie.name }}</td>
          <td v-if="currencie.balance > 0">{{ currencie.description }}</td>
          <td v-if="currencie.balance > 0">{{ parseFloat(currencie.balance.toFixed(currencie.decimals)) }}</td>
          <td v-if="currencie.balance > 0">US$ {{ parseFloat((currencie.balance * currencie.conversion.usd).toFixed(currencie.decimals)) }}</td>
          <td v-if="currencie.balance > 0">BTC {{ parseFloat((currencie.balance * currencie.conversion.btc).toFixed(currencie.decimals)) }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped>
.card {
  position: relative;
  width: 400px;
  height: 247px;
  
  border-radius: 20px;
  overflow: hidden;
  
  box-shadow: 5px 5px 5px rgba(0, 0, 0, 0.5);
}

.card > * {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.card__image {
  display: block;
}

.card__info {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  
  padding: 2em;
  opacity: 0;
  font-size: 20px;
  color: white;
  background-color: rgba(0, 0, 0, 0.5);
  
  transition: opacity 300ms ease;
}

.card:hover .card__info,
.card:focus-within .card__info {
  opacity: 1;
}

/* OTHER */

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  width: 100vw;
  height: 100vh;
  
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  
  background-color: #121420;
  color: white;
}

.table-scroll{
  width: 80vw;
  display: block;
  empty-cells: show;
  
  /* Decoration */
  border-spacing: 0;
  border: 1px solid;
}

.table-scroll thead{
  background-color: #f1f1f1;  
  position:relative;
  display: block;
  width:100%;
  overflow-y: scroll;
}

.table-scroll tbody{
  /* Position */
  display: block; position:relative;
  width:100%; overflow-y:scroll;
  /* Decoration */
  border-top: 1px solid rgba(0,0,0,0.2);
}

.table-scroll tr{
  width: 100%;
  display:flex;
}

.table-scroll td,.table-scroll th{
  flex-basis:100%;
  flex-grow:2;
  display: block;
  font-size: 1rem;
  padding: 1rem;
  text-align:left;
}

/* Other options */

.table-scroll.small-first-col td:first-child,
.table-scroll.small-first-col th:first-child{
  flex-basis:20%;
  flex-grow:1;
}

.table-scroll tbody tr:nth-child(2n){
  background-color: rgba(130,130,170,0.1);
}

.body-half-screen{
  max-height: 30vh;
}

.small-col{flex-basis:10%;}
</style>
