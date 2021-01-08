<template>
  <div id="app">
    <h1>Bitcoin Price Index</h1>
    <div
      v-for="(currency,idx) in info"
      class="currency"
      :key="idx"
    >

      <span class="lighten">
        {{ currency.description }}:
      <span v-html="currency.symbol"></span>      {{ currency.rate }}:
    </span>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Axios',
  data () {
    return {
      info: null
    }
  },
  mounted () {
    axios
      .get('https://api.coindesk.com/v1/bpi/currentprice.json')
      .then(response => (this.info = response.data.bpi))
  }
}
</script>

<style>

</style>
