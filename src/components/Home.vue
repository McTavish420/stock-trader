<template lang="html">
  <div class="container-fluid">
    <h1>Trade of view your Portfolio</h1>
    <h6>You may save & Load your Data</h6>
    <h6>Click on 'End Day' to begin a New Day!</h6>
    <hr>
    <p>Your Funds: {{funds | currency}}</p>
  </div>
</template>

<script>
export default {
  computed: {
    funds(){
      return this.$store.getters.funds;
    }
  }
}
</script>

<style lang="css" scoped>
</style>
