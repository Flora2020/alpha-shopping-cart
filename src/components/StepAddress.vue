<template>
  <div class="container">
    <div class="progress">
      <div class="step-one">
        <div class="done-block">
          <span class="number-bg-done">
            <span class="number-done">1</span>
          </span>
          寄送地址
        </div>

        <div class="progress-done"></div>

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
      <h3>寄送地址</h3>
      <form class="row g-3" @submit.prevent.stop="saveStorage">
        <div class="col-4">
          <label for="title" class="form-label">稱謂</label>
          <select v-model="title" name="title" id="title" class="form-select">
            <option value="先生" selected>先生</option>
            <option value="女士">女士</option>
            <option value="君">君</option>
          </select>
        </div>
        <div class="col-md-8">
          <label for="name" class="form-label">姓名</label>
          <input
            type="text"
            id="name"
            name="name"
            v-model="name"
            class="form-control"
            placeholder="請輸入姓名"
            required
          />
        </div>
        <div class="col-6">
          <label for="phone" class="form-label">電話</label>
          <input
            type="tel"
            id="phone"
            name="phone"
            v-model="phone"
            class="form-control"
            placeholder="請輸入行動電話"
            required
          />
        </div>
        <div class="col-6">
          <label for="eamil" class="form-label">Email</label>
          <input
            type="email"
            id="email"
            name="email"
            v-model="email"
            class="form-control"
            placeholder="請輸入電子郵件"
            required
          />
        </div>
        <div class="col-4">
          <label for="city" class="form-label">縣市</label>
          <select v-model="city" name="city" id="city" class="form-select">
            <option value="" selected>請選擇縣市</option>
            <option v-for="city in cities" :key="city.id" :value="city.name">
              {{ city.name }}
            </option>
          </select>
        </div>
        <div class="col-8 mb-4">
          <label for="address" class="form-label">地址</label>
          <input
            type="text"
            id="address"
            name="address"
            v-model="address"
            class="form-control"
            placeholder="請輸入地址"
            required
          />
        </div>
        <hr />
        <div class="col-4"></div>
        <div class="col-4"></div>
        <div class="col-4">
          <div class="d-grid gap-2">
            <button type="submit" class="btn btn-next">下一步 →</button>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
const STORAGE_KEY = 'alpha-shopping-cart'
// import { v4 as uuidv4 } from 'uuid'

export default {
  data () {
    return {
      title: '先生',
      name: '',
      phone: '',
      email: '',
      city: '',
      address: '',
      cities: [
        { id: 1, name: '基隆市' },
        { id: 2, name: '台北市' },
        { id: 3, name: '新北市' },
        { id: 4, name: '桃園縣' },
        { id: 5, name: '新竹市' },
        { id: 6, name: '新竹縣' },
        { id: 7, name: '苗栗縣' },
        { id: 8, name: '台中市' },
        { id: 9, name: '彰化縣' },
        { id: 10, name: '南投縣' },
        { id: 11, name: '雲林縣' },
        { id: 12, name: '嘉義市' },
        { id: 13, name: '嘉義縣' },
        { id: 14, name: '台南市' },
        { id: 15, name: '高雄市' },
        { id: 16, name: '屏東縣' },
        { id: 17, name: '台東縣' },
        { id: 18, name: '花蓮縣' },
        { id: 19, name: '宜蘭縣' },
        { id: 20, name: '澎湖縣' },
        { id: 21, name: '金門縣' },
        { id: 22, name: '連江縣' }
      ]
    }
  },

  methods: {
    saveStorage () {
      console.log('saveStorage')  //測試完可刪
      const data = {
        title: this.title,
        name: this.name,
        phone: this.phone,
        email: this.email,
        city: this.city,
        address: this.address
      }
      localStorage.setItem(STORAGE_KEY, JSON.stringify(data))
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
  /* margin: 0 3.5vw; */
  background: #2a2a2a;
}

.progress-undone {
  width: 5vw;
  height: 3px;
  /* margin: 0 3.5vw; */
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
  /* outline: 3px solid pink; */
}
</style>