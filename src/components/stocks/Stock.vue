<template lang="html">
  <div class="col-sm-6 col-md-4">
    <div class="card text-success">
      <div class="card-heading" style="background-color: lightgreen">
        <h3 class="card-title">
          {{stock.name}}
          <small>(Price: {{stock.price}})</small>
        </h3>
      </div>
      <div class="card-body">
        <div class="float-left">
          <input type="number"
                 class="form-control"
                 placeholder="Quantity"
                 v-model="quantity"
                 :class="{danger: insufficientFunds}">
        </div>
        <div class="float-right">
          <button class="btn btn-success"
                  @click="buyStock"
                  :disabled="(insufficientFunds) || (quantity <= 0) || (!Number.isInteger(Number(quantity)))"
                  >{{insufficientFunds ? 'Low Funds' : 'Buy'}}</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['stock'],
  data(){
    return {
      quantity: 0
    };
  },
  computed: {
    funds(){
      return this.$store.getters.funds;
    },
    insufficientFunds(){
      let total = this.quantity * this.stock.price;
      return total > this.funds;
    }
  },
  methods: {
    buyStock(){
      const order = {
        stockID: this.stock.id,
        stockPrice: this.stock.price,
        quantity: this.quantity
      };
      this.$store.dispatch('buyStock', order);
      this.quantity = 0;
    }
  }
}
</script>

<style lang="css" scoped>
.col-sm-6, .col-md-4 {
   padding: 5px;
}
.danger {
  border: 1px solid red;
}
</style>
