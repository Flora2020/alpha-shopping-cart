<template>
  <div class="footer">
    <div class="logo">
      <img src="../../public/image/logo.svg" alt="" />
      <p class="logo-title">ALPHA SHOP</p>
    </div>

    <div class="informations">
      <div class="information service">
        <p class="category">客戶服務</p>
        <ul>
          <li
            v-for="item in customerService"
            :key="item.id"
            class="category-item"
          >
            {{ item.name }}
          </li>
        </ul>
      </div>

      <div class="information about">
        <p class="category">關於我們</p>
        <ul>
          <li v-for="item in aboutUs" :key="item.id" class="category-item">
            {{ item.name }}
          </li>
        </ul>
      </div>

      <div class="information term">
        <p class="category">資訊</p>
        <ul>
          <li v-for="item in information" :key="item.id" class="category-item">
            {{ item.name }}
          </li>
        </ul>
      </div>

      <div class="information follow">
        <p class="category">追蹤 ALPHA SHOP</p>
        <ul>
          <li class="category-item">+886 02123-45678</li>
          <li class="category-item icon">
            <img
              class="icon facebook-icon"
              src="../../public/image/facebook-f-brands.svg"
              alt=""
            />
            <img
              class="icon instagram-icon"
              src="../../public/image/instagram-brands.svg"
              alt=""
            />
            <img
              class="icon whatsapp-icon"
              src="../../public/image/whatsapp-brands.svg"
              alt=""
            />
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid'

export default {
  data () {
    return {
      customerService:
        [
          { id: uuidv4(), name: '運送說明' },
          { id: uuidv4(), name: '退換貨相關' },
          { id: uuidv4(), name: '付款資訊' },
          { id: uuidv4(), name: 'FAQ' }
        ],

      aboutUs: [
        { id: uuidv4(), name: '品牌故事' },
        { id: uuidv4(), name: '媒體聯繫' },
        { id: uuidv4(), name: 'Press kit' }
      ],

      information: [
        { id: uuidv4(), name: '隱私權政策' },
        { id: uuidv4(), name: 'Cookie' },
        { id: uuidv4(), name: 'GDPR' }
      ]
    }
  }

}
</script>


<style>
.footer {
  display: flex;
  background: #e5e5e5;
}

.logo,
.informations {
  display: flex;
}

.logo,
.information {
  margin: 30px;
}

.information {
  display: flex;
  flex-direction: column;
}
.logo {
  width: 175.49px;
  height: 31px;
}

.information .service {
  width: 96px;
  height: 140px;
}

.information .about {
  width: 96px;
  height: 115px;
}

.information .term {
  width: 84px;
  height: 115px;
}

.information .follow {
  width: 199px;
  height: 96px;
}

ul {
  list-style-type: none;
}

.information ul .icon {
  display: flex;
}

img {
  display: block;
}

.icon {
  height: 20px;
}
</style>
