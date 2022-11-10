<template>
  <div class="d-flex flex-row">
    <OrderView />
    <div class="between"></div>
    <OrderBook />
  </div>
</template>

<script>
import OrderView from './components/Order.vue'
import OrderBook from './components/OrderBook.vue'

export default {
  name: 'App',
  components: {
    OrderView,
    OrderBook,
  }
}
</script>

<style scoped>
  div.between {
    background-color: #000000;
    width: 3px;
    height: 100vh;
  }
</style>
