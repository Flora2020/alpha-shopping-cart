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
        <ShoppingCart />
      </div>
    </div>
  </div>
</template>

<script>
import StepAddress from '../components/StepAddress.vue'
import ShoppingCart from '../components/ShoppingCart.vue'

export default {
  components: {
    StepAddress,
    ShoppingCart
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