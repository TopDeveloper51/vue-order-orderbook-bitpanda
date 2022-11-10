<template>
  <div class="order-book-container">
    <div class="d-flex align-items-center title-bar">
      <div class="ml-2 title">ORDER BOOK</div>
    </div>
    <div class="d-flex align-items-center pr-2 pl-2 table-header">
        <div class="table-header-cell">Total</div>
        <div class="table-header-cell">Amount</div>
        <div class="table-header-cell">Price</div>
      </div>
    <div class="order-book-table">
      <div class="order-book-side1">
        <div v-for="n in 30" v-bind:key="n" class="d-flex align-items-center pr-2 pl-2 table-body">
          <div class="table-body-total">{{12313 + n}}</div>
          <div class="table-body-amount">{{123123 + n}}</div>
          <div class="table-body-price">{{123132 + n}}</div>
        </div>
      </div>
      <div class="seperator p-2">
        <div class="d-flex justify-content-between">
          <div class="seperator-label">
            LAST MATCHED PRICE
          </div>
          <div class="seperator-value">
            17400.00
          </div>
        </div>
        <div class="d-flex justify-content-between">
          <div class="seperator-label">
            CURRENT SPREAD
          </div>
          <div class="seperator-value">
            28.82
          </div>
        </div>
        <div class="d-flex justify-content-between">
          <div class="seperator-label">
            COMPILE
          </div>
          <div class="d-flex align-items-center">
            <b-icon :icon="this.plusHoverHandler()" class="compile-icon" @click="plusHover = true; dashHover = false"></b-icon>
            <div class="compile-value">
              {{compileValue}}
            </div>
            <b-icon :icon="this.dashHoverHandler()" class="compile-icon" @click="plusHover = false; dashHover = true"></b-icon>
          </div>
        </div>
      </div>
      <div class="order-book-side2">
        <div v-for="n in 30" v-bind:key="n" class="d-flex align-items-center pr-2 pl-2 table-body">
          <div class="table-body-total">{{12313 + n}}</div>
          <div class="table-body-amount">{{123132 + n}}</div>
          <div class="table-body-price1">{{123123 + n}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'OrderView',
  components: {
  },
  props: {
  },
  data() {
    return {
      value: 0,
      plusHover: false,
      dashHover: false,
      compileValue: 1,
    }
  },
  methods: {
    plusHoverHandler() {
      if (this.plusHover === true) {
        return "plus-square-fill";
      } else {
        return "plus-square";
      }
    },
    dashHoverHandler() {
      if (this.dashHover === true) {
        return "dash-square-fill";
      } else {
        return "dash-square";
      }
    }
  }
}
</script>

<style scoped>
  div.title {
    font-size: 15px;
    font-weight: 600;
    color: #E5E6E7;
    font-family: inherit;
  }
  div.title-bar {
    height: 48px;
    background-color: #0F1217;
  }
  div.order-book-container {
    width: 260px;
    height: 100vh;
  }
  div.order-book-table {
    width: 260px;
    height: calc(100vh - 67.5px);
    overflow: scroll;
    background-color: #15181F;
  }
  div.order-book-table::-webkit-scrollbar {
    display: none;
  }
  div.table-header {
    background-color: #15181F;
  }
  div.table-body {
    background-color: #22242B;
  }
  div.table-header-cell {
    color: #737679;
    text-align: right;
    width: calc(100vw / 3);
    font-size: 13px;
    font-family: inherit;
  }
  div.table-body-total {
    text-align: right;
    color: #969A9E;
    font-size: 13px;
    font-family: inherit;
    width: calc(100vw / 3);
  }
  div.table-body-amount {
    text-align: right;
    color: #E2E3E4;
    font-size: 13px;
    font-family: inherit;
    width: calc(100vw / 3);
  }
  div.table-body-price {
    text-align: right;
    color: #FD4F4F;
    font-size: 13px;
    font-family: inherit;
    width: calc(100vw / 3);
  }
  div.table-body-price1 {
    text-align: right;
    color: #2FBF7A;
    font-size: 13px;
    font-family: inherit;
    width: calc(100vw / 3);
  }
  div.seperator-label {
    color: #B2B4B7;
    font-size: 13px;
    font-family: inherit;
  }
  div.seperator-value {
    color: #E2E3E4;
    font-size: 13px;
    font-family: inherit;
  }
  div.seperator {
    width: 100%;
    background-color: #0F1217;
    position: sticky;
    bottom: 0;
    top: 0;
  }
  div.order-book-side1 {
    /* position: relative; */
    flex-direction: column-reverse;
    display: flex;
  }
  div.order-book-side2 {
    /* position: relative; */
    flex-direction: column;
    display: flex;
  }
  div.orderbook-aggregation__button {
    color: #a1a5a9;
  }
  div.compile-value {
    width: 80px;
    text-align: center;
    color: #E2E3E4;
    font-size: 13px;
    font-family: inherit;
  }
  .compile-icon {
    color: #A1A5A9;
    width: 12px;
    height: 12px;
  }
</style>
