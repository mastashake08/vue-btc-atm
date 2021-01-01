<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-img
          :src="require('../assets/logo.svg')"
          class="my-3"
          contain
          height="200"
        />
      </v-col>

      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">
          J Computer Solutions LLC BTC ATM
        </h1>
        <BTCPrice :price="current_price"/>
      </v-col>
    </v-row>
    <v-row class="text-center">
      <v-col>
        <Buy :price="buy_price"/>
      </v-col>
      <v-col>
        <Sell :price="sell_price"/>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import BTCPrice from './BTCPrice'
import Buy from './Buy'
import Sell from './Sell'
import axios from 'axios'
  export default {
    name: 'Main',
    components: {
      BTCPrice,
      Buy,
      Sell
    },
    data: () => ({
      sell_price: 0,
      buy_price: 0,
      current_price: 0
    }),
    created() {
      let that = this
      axios.get('https://blockchain.info/ticker').then(data => {
        that.sell_price = (data.data.USD.sell * 0.9).toFixed(2)
        that.buy_price = (data.data.USD.buy * 1.1).toFixed(2)
        that.current_price = (data.data.USD.last).toFixed(2)
      })
    }
  }
</script>
