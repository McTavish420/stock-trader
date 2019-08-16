<template lang="html">
  <div class="container">
    <div class="row">
        <app-stock class="col" v-for="stock in stocks" :stock="stock"></app-stock>
    </div>
  </div>
</template>

<script>
import {mapGetters} from 'vuex';
import Stock from './Stock.vue';
export default {
  computed: {
    ...mapGetters({
      stocks: 'stockPortfolio'
    })
  },
  components: {
    appStock: Stock
  }
}
</script>

<style lang="css" scoped>
</style>
