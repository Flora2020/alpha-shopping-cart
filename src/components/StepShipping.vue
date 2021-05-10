<template>
  <div class="container">
    <div class="progress">
      <div class="step-one">
        <div class="done-block">
          <span class="number-bg-done">
            <span class="number-done">✔</span>
          </span>
          寄送地址
        </div>

        <div class="progress-done"></div>
        <!-- TODO: 修改運送方式樣式 -->
        <div class="undone-block">
          <span class="number-bg-undone">
            <span class="number-undone">2</span>
          </span>
          運送方式
        </div>

        <div class="progress-undone"></div>

        <div class="undone-block">
          <span class="number-bg-undone">
            <span class="number-undone">3</span>
          </span>
          付款資訊
        </div>
      </div>
    </div>
    <div class="address">
      <h3>運送方式</h3>
      <form class="row g-3">
        <div class="col-12">
          <!-- TODO: 修改 checkbox 樣式 -->
          <div
            class="form-check"
            v-for="option in shippingOptions"
            :key="option.id"
          >
            <input
              class="form-check-input"
              type="radio"
              v-model="checkedShippingId"
              name="shipping"
              :id="option.enName"
              :value="option.id"
            />
            <label class="form-check-label" :for="option.enName">
              <div class="left">
                <p>{{ option.name }}</p>
                <p>{{ option.time }}</p>
              </div>
              <div class="right">
                {{
                  option.fee === 0
                    ? "免費"
                    : "$" +
                      option.fee
                        .toString()
                        .replace(/\B(?=(\d{3})+(?!\d))/g, ",")
                }}
              </div>
            </label>
          </div>
        </div>
        <hr />
        <div class="col-4 p-0">
          <!-- TODO: 修改上一步按鈕樣式 -->
          <button
            class="btn btn-text px-0"
            @click.prevent.stop="onClickBackToStepOne()"
          >
            ← 上一步
          </button>
        </div>
        <div class="col-4"></div>
        <div class="col-4 p-0">
          <div class="d-grid gap-2">
            <button
              type="submit"
              class="btn btn-next"
              @click.prevent.stop="onClickStepThree()"
            >
              下一步 →
            </button>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    STORAGE_KEY: {
      type: String,
      required: true
    },

    shippingOptions: {
      type: Array,
      required: true
    }
  },

  data () {
    return {
      checkedShippingId: 1
    }
  },

  created () {
    // TODO: 使用者點選上一步，並點選下一步回到此頁後，運送方式沒有勾選在相應的位置
    const data = JSON.parse(localStorage.getItem(this.STORAGE_KEY))
    if (!data || !data.shipping) { return }
    this.checkedShippingId = data.shipping.id
  },

  methods: {
    onClickBackToStepOne () {
      this.$emit('after-click-back-to-step-address')
    },

    onClickStepThree () {
      this.$emit('after-click-step-checkout')
    }
  },

  watch: {
    checkedShippingId:
      function handleCheckeShippingOption () {
        this.$emit('after-check-shipping-option', this.checkedShippingId)
      }
  }
}
</script>


<style>
.container {
  padding: 0;
}

.progress {
  width: 100%;
  height: 24px;
  background: #ffffff;
}

.step-one {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.step-one div {
  line-height: 24px;
  font-size: 18px;
}

.done-block {
  color: #2a2a2a;
}

.undone-block {
  color: #afb1bd;
}

.number-bg-done {
  border-radius: 50%;
  height: 24px;
  width: 24px;
  margin-right: 5px;
  display: inline-block;
  background: #2a2a2a;
  vertical-align: top;
}

.number-bg-undone {
  border-radius: 50%;
  border: 2px solid #afb1bd;
  height: 24px;
  width: 24px;
  margin-right: 5px;
  display: inline-block;
  vertical-align: top;
}

.number-done {
  display: block;
  height: 24px;
  line-height: 24px;
  text-align: center;
  font-weight: bolder;
  color: #ffffff;
}

.number-undone {
  display: block;
  height: 24px;
  line-height: 20px;
  text-align: center;
  font-weight: bold;
  color: #afb1bd;
}

.progress-done {
  width: 5vw;
  height: 3px;
  background: #2a2a2a;
}

.progress-undone {
  width: 5vw;
  height: 3px;
  background: #afb1bd;
}

h3 {
  margin: 30px 0;
  font-size: 24px;
  line-height: 24px;
  font-weight: 700;
}

hr {
  border: 1px solid #f0f0f5;
  opacity: 1;
}

.btn-next {
  width: 100%;
  background: #f67599;
  color: #ffffff;
}
</style>