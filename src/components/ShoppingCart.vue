<template>
  <div class="container cart-container">
    <div class="row">
      <div class="col-12">
        <h4>購物籃</h4>
      </div>
      <div class="col-12">
        <div
          class="cart-item d-flex justify-content-between mb-4"
          v-for="good in goods"
          :key="good.id"
        >
          <div class="cart-item-left d-flex justify-content-between">
            <img :src="good.img" alt="" />
            <div class="cart-item-info ps-3">
              <p class="mb-3">{{ good.name }}</p>
              <div class="count-box d-flex justify-content-between">
                <MinusButton @click.native="onClickMinus(good.id - 1)" />
                <div class="count" v-text="good.count"></div>
                <PlusButton @click.native="onClickPlus(good.id - 1)" />
              </div>
            </div>
          </div>
          <div class="cart-item-right">
            {{
              "$" + good.price.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",")
            }}
          </div>
        </div>
      </div>
      <div class="col-12">
        <div class="cart-details d-flex justify-content-between">
          <div class="cart-details-left">運費</div>
          <div class="cart-details-right">免費</div>
        </div>
      </div>
      <div class="col-12">
        <div class="cart-details d-flex justify-content-between">
          <div class="cart-details-left">小計</div>
          <div class="cart-details-right">
            {{
              "$" + subtotal.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",")
            }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
import PlusButton from './PlusButton.vue'
import MinusButton from './MinusButton.vue'

export default {
  components: {
    PlusButton,
    MinusButton
  },

  props: {
    subtotal: {
      type: Number,
      required: true
    },

    goods: {
      type: Array,
      required: true
    }
  },

  methods: {
    onClickPlus (goodIndex) {
      this.$emit('after-click-plus', goodIndex)
      return
    },

    onClickMinus (goodIndex) {
      this.$emit('after-click-minus', goodIndex)
      return
    }
  }
}
</script>

<style>
.cart-container {
  padding: 32px 24px;
  border: 1px solid #f0f0f5;
  border-radius: 8px;
}

h4 {
  margin-bottom: 30px;
  line-height: 22px;
  font-size: 18px;
  font-weight: 700;
}

.cart-item-left img {
  width: 100px;
  height: 100px;
  border-radius: 4px;
}

.cart-item-info .count-box {
  width: 116px;
  height: 27px;
}

.count {
  line-height: 27px;
}

.cart-details {
  margin: 32px 0 0;
  padding-top: 20px;
  border-top: 1px solid #f0f0f5;
}
</style>