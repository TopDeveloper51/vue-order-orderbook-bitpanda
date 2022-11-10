<template>
  <div class="order-container">
    <div class="d-flex align-items-center title-bar">
      <div class="ml-2 title">ORDER</div>
      <div class="d-flex flex-row ml-auto">
        <div @click="selectedNavBtn = 'Market'" class="mr-3" :class="this.changeMarketNavStyle()">
          Market
        </div>
        <div @click="selectedNavBtn = 'Limit'" class="mr-2" :class="this.changeLimitNavStyle()">
          Limit
        </div>
      </div>
    </div>
    <div class="d-flex align-items-center button-container">
      <button @click="buyOrSell = 'buy'" type="button" class="btn ml-2" :class="this.selectBuy()">BUY</button>
      <button @click="buyOrSell = 'sell'" type="button" class="btn mr-2" :class="this.selectSell()">SELL</button>
    </div>
    <div class="ml-2 mr-2" autocomplete="off">
      <div class="d-flex justify-content-between pb-1">
        <div class="balance-text">
          Available:
        </div>
        <div class="balance-text1">
          {{'0.00'}} EUR
        </div>
      </div>
      <div class="d-flex justify-content-between pb-3 second-balance">
        <div class="balance-text">
          Locked:
        </div>
        <div class="balance-text1">
          {{'0.00'}} EUR
        </div>
      </div>
      <div class="d-flex justify-content-between pt-2 pb-4">
        <div class="limit-text">
          Limit price:
        </div>
        <div class="limit-text1">
          <input type="text" class="limit-input" v-model="limitPrice" @change="changeAmount()"/> EUR
        </div>
      </div>
      <div class="d-flex justify-content-between pt-3 pb-1">
        <div class="limit-text">
          Amount:
        </div>
        <div class="limit-text1">
          <input type="text" class="limit-input" v-model="amount" @change="changeAmount()"/> BTC
        </div>
      </div>
      <div class="mb-4">
        <div class="d-flex align-items-center">
          <div class="stepper-cell"></div>
          <div class="stepper-cell"></div>
          <div class="stepper-cell"></div>
          <div class="stepper-cell"></div>
        </div>
        <div class="d-flex align-items-center justify-content-between">
          <div class="stepper-point"></div>
          <div class="stepper-point"></div>
          <div class="stepper-point"></div>
          <div class="stepper-point"></div>
          <div class="stepper-point"></div>
        </div>
        <div class="d-flex align-items-center justify-content-between">
          <div class="step-label">0%</div>
          <div class="step-label">25%</div>
          <div class="step-label">50%</div>
          <div class="step-label">75%</div>
          <div class="step-label">100%</div>
        </div>
      </div>
      <div class="d-flex justify-content-between pt-2 pb-5">
        <div class="limit-text">
          Total:
        </div>
        <div class="limit-text1">
          <input type="text" class="limit-input" v-model="totalPrice"/> EUR
        </div>
      </div>
    </div>
    <div v-if="selectedNavBtn === 'Limit'" class="d-flex justify-content-between align-items-center p-2 advanced-border">
      <div class="limit-text">
        Advanced:
      </div>
      <b-icon :icon="this.checkHoverHandler()" class="advanced-check" @click="checkHover === true ? checkHover = false : checkHover = true"></b-icon>
    </div>
    <div class="d-flex justify-content-between pb-1 pt-3 pr-2 pl-2">
      <div class="balance-text">
        Fee(-%)
      </div>
      <div class="balance-text1">
        {{'0.00000000'}} BTC
      </div>
    </div>
    <div class="d-flex justify-content-between pb-4 pr-2 pl-2">
      <div class="balance-text">
        Total (excl. fees)
      </div>
      <div class="balance-text1">
        {{'0.54356000'}} BTC
      </div>
    </div>
    <div class="ml-2 mr-2">
      <button type="button" class="btn buy-btc-btn" :class="this.changeColor()">
        {{buyOrSell === 'buy' ? 'BUY BTC' : 'SELL BTC'}}
      </button>
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
      sliderLabels: [
        '0%',
        '25%',
        '50%',
        '75%',
        '100%',
      ],
      checkHover: false,
      amount: 0.0000,
      limitPrice: 17000.02,
      totalPrice: 0,
      selectedNavBtn: 'Market',
      buyOrSell: 'buy',
    }
  },
  methods: {
    checkHoverHandler() {
      if (this.checkHover === true) {
        return "check-square";
      } else {
        return "square";
      }
    },
    changeAmount() {
      console.log('eeee');
      this.totalPrice = this.limitPrice * this.amount;
    },
    changeColor() {
      if (this.totalPrice === 0) {
        return 'buy-btc-btn1';
      } else {
        if (this.buyOrSell === 'buy') {
          return 'buy-btc-btn2';
        } else {
          return 'sell-btc-btn2';
        }
        
      }
    },
    changeMarketNavStyle() {
      if (this.selectedNavBtn === 'Market') {
        return 'selected-nav-btn';
      } else {
        return 'nav-btn';
      }
    },
    changeLimitNavStyle() {
      if (this.selectedNavBtn === 'Limit') {
        return 'selected-nav-btn';
      } else {
        return 'nav-btn';
      }
    },
    selectBuy() {
      if (this.buyOrSell === 'buy') {
        return 'buy-btn';
      } else {
        return 'disable-btn';
      }
    },
    selectSell() {
      if (this.buyOrSell === 'sell') {
        return 'sell-btn';
      } else {
        return 'disable-btn';
      }
    },
  }
}
</script>

<style scoped>
  div.nav-btn {
    border-bottom: solid 2px #292B34;
    font-family: inherit;
    font-size: 14px;
    font-weight: 600;
    color: #B0B2B6;
  }
  div.selected-nav-btn {
    border-bottom: solid 2px #53DA99;
    font-family: inherit;
    font-size: 14px;
    font-weight: 600;
    color: #E5E6E7;
  }
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
  div.order-container {
    width: 260px;
    height: 100vh;
    background-color: #15181F;
    overflow: hidden;
  }
  button.buy-btn {
    width: 50%;
    height: 38.8px;
    border-top-right-radius: 0;
    border-bottom-right-radius: 0;
    border-bottom-left-radius: 2px;
    border-top-left-radius: 2px;
    background-color: #53DA99;
    color: #23294D;
    font-family: inherit;
    font-size: 14px;
    font-weight: 600;
  }
  button.sell-btn {
    width: 50%;
    height: 38.8px;
    border-top-left-radius: 0;
    border-bottom-left-radius: 0;
    border-top-right-radius: 2px;
    border-bottom-right-radius: 2px;
    background-color: #FF6150;
    color: #E5E6E7;
    font-family: inherit;
    font-size: 14px;
    font-weight: 600;
  }
  button.disable-btn {
    width: 50%;
    height: 38.8px;
    border-top-left-radius: 0;
    border-bottom-left-radius: 0;
    border-top-right-radius: 2px;
    border-bottom-right-radius: 2px;
    background-color: #3A3C42;
    color: #E5E6E7;
    font-family: inherit;
    font-size: 14px;
    font-weight: 600;
  }
  div.button-container {
    height: 73.8px;
  }
  div.balance-text {
    color: #B2B4B7;
    font-size: 13px;
    font-family: inherit;
  }
  div.balance-text1 {
    color: #B2B4B7;
    font-size: 13px;
    font-weight: 500;
    font-family: inherit;
  }
  div.second-balance {
    border-bottom: solid 1px #2d3036
  }
  div.limit-text {
    font-size: 15px;
    color: #B2B4B7;
    font-weight: 500;
    font-family: inherit;
  }
  div.limit-text1 {
    font-size: 14px;
    color: #B2B4B7;
    font-family: inherit;
  }
  div.advanced-border {
    border-top: solid 1px #2d3036;
    border-bottom: solid 1px #2d3036;
  }
  button.buy-btc-btn1 {
    width: 100%;
    height: 44.19px;
    background-color: #1A1C21;
    color: #868789;
    font-size: 17px;
    font-weight: 600;
    font-family: inherit;
    border-radius: 2px;
    border: solid 1px #9E9FA2;
  }
  button.buy-btc-btn2 {
    width: 100%;
    height: 44.19px;
    background-color: #53DA99;
    color: #23294D;
    font-size: 17px;
    font-weight: 600;
    font-family: inherit;
    border-radius: 2px;
  }
  button.sell-btc-btn2 {
    width: 100%;
    height: 44.19px;
    background-color: #FF6150;
    color: #E5E6E7;
    font-size: 17px;
    font-weight: 600;
    font-family: inherit;
    border-radius: 2px;
  }
  input.limit-input {
    width: 130px;
    background-color: #15181F;
    border: 0;
    direction: rtl;
    color: #E5E6E7;
    font-size: 17px;
    font-weight: 700;
  }
  input.limit-input:focus {
    outline: none;
  }
  div.stepper-cell {
    width: calc(100vh / 4);
    height: 4px;
    background-color: #26292E;
  }
  div.stepper-point {
    width: 6px;
    height: 6px;
    border-radius: 3px;
    background-color: #67686D;
    position: relative;
    top: -5px;
  }
  div.step-label {
    color: #606369;
    font-size: 13px;
    font-family: inherit;
  }
  .advanced-check {
    color: #A1A5A9;
    width: 14px;
    height: 14px;
  }
</style>
