<template>
<header>
  <h3 style="color: black">{{ title }}</h3>
</header>
  <body>
<div class="input-container">
  <input v-model="inputValue" class="currency-input" type="text">
</div>
  <div class="currency-radio">
    <input v-model="money" class="radio-input" type="radio" name="currency" checked>
    <label>Dollars</label>
    <input v-model="money" class="radio-input" type="radio" name="currency">
    <label>Euros</label>
    <input v-model="money" class="radio-input" type="radio" name="currency">
    <label>Pounds</label>
  </div>
  <div class="currency-buttons">
    <button @click="buyCurrency">Buy</button>
    <button @click="saleCurrency">Sale</button>
  </div>
  <div class="currency-result">
    <p></p>
  </div>
  </body>
  <Axios/>
</template>

<script>
import Axios from './Axios.vue'

export default {
  name: 'Currency',
  data () {
    return {
      title: 'This is currency page',
      inputValue: '',
      money: ''
    }
  },
  methods: {
    buyCurrency () {
      console.log(1)
    },
    saleCurrency () {
      console.log(2)
    }
  },
  components: {
    Axios
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
  padding: 10px 10px;
  background-color: lightgray;
  border: 1px solid gray;
  border-radius: 5px;
}

.currency-input{
  padding: 10px;
}
.currency-radio{
  margin-top: 10px;
  padding: 3px;
  width: 320px;
  border: 1px solid gray;
  border-radius: 15px;
}
.radio-input{
margin: 5px 15px;
}
.currency-buttons{
  margin-top: 10px;
}
.currency-result{
  margin-top: 10px;
  padding: 3px;
  height: 24px;
  width: 320px;
  border: 1px solid gray;
  border-radius: 15px;
}
</style>
