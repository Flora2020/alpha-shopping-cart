<template>
  <div class="container">
    <h1>結帳</h1>
    <div class="row">
      <div class="col-6">
        <div class="step">
          <StepAddress
            v-if="isStepAddress"
            :STORAGE_KEY="STORAGE_KEY"
            @after-click-step-shipping="goToStepShipping"
          />
          <StepShipping
            v-if="isStepShipping"
            :STORAGE_KEY="STORAGE_KEY"
            :shippingOptions="shippingOptions"
            @after-check-shipping-option="renewShippingFee"
            @after-click-step-checkout="goToStepCheckout"
            @after-click-back-to-step-address="goBackToStepAddress"
          />
          <StepCheckout v-if="isStepCheckout" />
        </div>
      </div>
      <div class="col-1"></div>
      <div class="col-5">
        <ShoppingCart
          :goods="goods"
          :subtotal="subtotal"
          :shippingFee="shippingFee"
          @after-click-plus="afterClickPlus"
          @after-click-minus="afterClickMinus"
        />
      </div>
    </div>
  </div>
</template>

<script>
import StepAddress from '../components/StepAddress.vue'
import StepShipping from '../components/StepShipping.vue'
import StepCheckout from '../components/StepCheckout.vue'
import ShoppingCart from '../components/ShoppingCart.vue'

const STORAGE_KEY = 'alpha-shopping-cart'

const goods = [
  { id: 1, name: '破壞補丁修身牛仔褲', price: 3999, img: 'https://i.imgur.com/vkTyol5.png', count: 0 },
  { id: 2, name: '刷色直筒牛仔褲', price: 1299, img: 'https://i.imgur.com/NlkmoSk.png', count: 0 },
]

const shippingOptions = [
  { id: 1, name: '標準運送', enName: 'standard', time: '約 3~7 個工作天', fee: 0 },
  { id: 2, name: 'DHL 貨運', enName: 'dhl', time: '48 小時內送達', fee: 500 }
]

export default {
  components: {
    StepAddress,
    StepShipping,
    StepCheckout,
    ShoppingCart
  },

  data () {
    return {
      isStepAddress: true,
      isStepShipping: false,
      isStepCheckout: false,
      STORAGE_KEY,
      goods: [],
      shippingOptions: [],
      goodsPrice: 0,
      shippingFee: 0,
      subtotal: 0
    }
  },

  created () {
    this.fetchGoods()
    this.fetchShippingOptions()
  },

  methods: {
    fetchGoods () {
      this.goods = goods
    },

    fetchShippingOptions () {
      this.shippingOptions = shippingOptions
    },

    afterClickPlus (goodIndex) {
      this.goods[goodIndex].count++

      this.goodsPrice += this.goods[goodIndex].price
      this.subtotal = this.goodsPrice + this.shippingFee
      return
    },

    afterClickMinus (goodIndex) {
      if (this.goods[goodIndex].count === 0) {
        return
      }
      this.goods[goodIndex].count--

      if (this.goods[goodIndex].price === 0) {
        return
      }
      this.goodsPrice -= this.goods[goodIndex].price
      this.subtotal = this.goodsPrice + this.shippingFee
      return
    },

    renewShippingFee (shippingId) {
      const data = JSON.parse(localStorage.getItem(this.STORAGE_KEY))
      const selectedShippingOption = this.shippingOptions.find(option => option.id === shippingId)
      data.shipping = {
        id: shippingId,
        name: selectedShippingOption.name
      }
      this.shippingFee = selectedShippingOption.fee
      this.subtotal = this.goodsPrice + this.shippingFee
      localStorage.setItem(this.STORAGE_KEY, JSON.stringify(data))
    },

    goToStepShipping () {
      this.isStepAddress = false
      this.isStepShipping = true
      this.isStepCheckout = false
    },

    goToStepCheckout () {
      this.isStepAddress = false
      this.isStepShipping = false
      this.isStepCheckout = true
    },

    goBackToStepAddress () {
      this.isStepAddress = true
      this.isStepShipping = false
      this.isStepCheckout = false
    }
  }
}
</script>


<style >
html,
body {
  background: #ffffff;
  font-family: "Noto Sans TC", sans-serif;
  color: #2a2a2a;
}
h1 {
  margin: 50px 0;
  font-size: 32px;
  line-height: 38px;
  font-weight: 700;
}
</style>