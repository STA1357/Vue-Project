<template>
<header>
  <div class="bit">
    <i class='fas fa-file-invoice-dollar animate__animated'
       @mouseover="isHovering = true"
       @mouseout="isHovering = false"
       @click= "isBuy = !isBuy; changeTitle()"
       :class="{animate__rotateIn: isHovering}">
    </i>
  </div>
  <h3 style="color: black">{{ title }}
  </h3>
</header>

  <body>
<div class="input-container">
  <input v-model="inputValue" class="currency-input" type="text" placeholder="Type the number of BitCoins">
</div>
  <div class="choose-currency">
    <button @click="useUsd" class="btn" id="btn-usd">USD</button>
    <button @click="usePst" class="btn" id="btn-gbp">GBP</button>
    <button @click="useEur" class="btn" id="btn-eur">EUR</button>
  </div>
  <div class="currency-buttons">
    <button @click="buyCurrency" class="buyCurrency">Buy</button>
    <button @click="saleCurrency" class="saleCurrency">Sale</button>
  </div>
  <div class="currency-result">
    {{moneyData}}
  </div>
  </body>
  <Axios/>
</template>

<script>
import Axios from './Axios.vue'
import axios from 'axios'

export default {
  name: 'Currency',
  data () {
    return {
      title: 'Exchange the Bit Coins',
      inputValue: '',
      moneyData: 0,
      money: 0,
      info: null,
      isHovering: false,
      isBuy: true
    }
  },
  methods: {
    changeTitle () {
      if (this.isBuy) {
        this.title = 'Exchange the Bit Coins'
        console.log(this.title)
      } else {
        this.title = 'Buy the Bit Coins'
      }
    },
    buyCurrency () {
      this.moneyData = this.money
      this.inputValue = ''
    },
    saleCurrency () {
      this.moneyData = (parseInt(this.money) / 100) * 99
      this.inputValue = ''
    },
    useUsd () {
      if (this.isBuy) {
        this.money = this.inputValue * this.info.USD.rate_float + ' USD'
      } else {
        this.money = this.inputValue / this.info.USD.rate_float + ' BTC'
      }
    },
    useEur () {
      if (this.isBuy) {
        this.money = this.inputValue * this.info.EUR.rate_float + ' EUR'
      } else {
        this.money = this.inputValue / this.info.EUR.rate_float + ' BTC'
      }
    },
    usePst () {
      if (this.isBuy) {
        this.money = this.inputValue * this.info.GBP.rate_float + ' GBP'
      } else {
        this.money = this.inputValue / this.info.GBP.rate_float + ' BTC'
      }
    }
  },
  components: {
    Axios
  },
  mounted () {
    axios
      .get('https://api.coindesk.com/v1/bpi/currentprice.json')
      .then(response => (this.info = response.data.bpi))
  }
}
</script>

<style>
body{
  display: flex;
  justify-content: center;
  justify-content: space-between;
  align-items: center;
  flex-direction: column;
}

.input-container{
  width: 300px;
  padding: 5px 10px;
  background-color: lavender;
  border: 1px solid gray;
  border-radius: 20px;
}

.currency-input{
  padding: 10px;
}
.choose-currency{
margin: 20px 15px;
}
.currency-buttons{
  margin-top: 0;
}
.currency-result{
  margin-top: 15px;
  padding: 3px;
  min-height: 22px;
  width: 315px;
  border: 1px solid gray;
  border-radius: 15px;
}

.btn:focus{
  background-color: #0F2F31;
  color: lightgray;
}

#btn-usd{
width: 108px;
  height: 32px;
  border-radius: 15px 0 0 15px;
  outline: none;
  border: 1px solid grey;
}
#btn-eur{
  width: 108px;
  height: 32px;
  border-radius: 0 15px 15px 0;
  outline: none;
  border: 1px solid grey;
}
#btn-gbp{
  width: 108px;
  height: 32px;
  outline: none;
  border: 1px solid grey;
  border-radius: 0;
}

.buyCurrency{
  height: 32px;
  width: 160px;
  border-radius: 15px 0 0 15px;
  outline: none;
  border: 1px solid grey;
}
.buyCurrency:hover{
  background-color: #0F2F31;
  color: white;
  transition: all .4s ease;
}
.saleCurrency{
  height: 32px;
  width: 160px;
  border-radius: 0 15px 15px 0;
  outline: none;
  border: 1px solid grey;
}
.saleCurrency:hover{
  background-color: #0F2F31;
  color: white;
  transition: all .4s ease;
}
i{
  font-size: 26px;
}
</style>
