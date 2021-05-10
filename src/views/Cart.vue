<template>
  <div class="container">
    <h1>結帳</h1>
    <div class="row">
      <div class="col-6">
        <div class="step">
          <StepAddress />
        </div>
      </div>
      <div class="col-1"></div>
      <div class="col-5">
        <ShoppingCart
          :goods="goods"
          :subtotal="subtotal"
          @after-click-plus="afterClickPlus"
          @after-click-minus="afterClickMinus"
        />
      </div>
    </div>
  </div>
</template>

<script>
import StepAddress from '../components/StepAddress.vue'
import ShoppingCart from '../components/ShoppingCart.vue'

const goods = [
  { id: 1, name: '破壞補丁修身牛仔褲', price: 3999, img: 'https://i.imgur.com/vkTyol5.png', count: 0 },
  { id: 2, name: '刷色直筒牛仔褲', price: 1299, img: 'https://i.imgur.com/NlkmoSk.png', count: 0 },
]

export default {
  components: {
    StepAddress,
    ShoppingCart
  },

  data () {
    return {
      subtotal: 0,
      goods: []
    }
  },

  created () {
    this.fetchGoods()
  },

  methods: {
    fetchGoods () {
      this.goods = goods
    },

    afterClickPlus (goodIndex) {
      this.goods[goodIndex].count++

      this.subtotal += this.goods[goodIndex].price
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
      this.subtotal -= this.goods[goodIndex].price
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