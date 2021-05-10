# alpha-shopping-cart
此專案是因為參加「測試 Alpha Camp 課程作業」，以及為了熟悉 Vue 的操作，以便培養與前端工程師的合作能力而寫的。

## 環境建置與需求 (prerequisites)

#### 框架 (frameworks) 
- Vue 2
- @vue/cli-service 4.5.0
- bootstrap 5.0.0

## 本地安裝（local install）
1. Download repo: `git clone https://github.com/Flora2020/alpha-shopping-cart.git`
2. Move to repo folder: `cd talpha-shopping-cart`
3. Install package: `npm install`
4. start server: `npm run serve`

## 開發紀錄
#### 每個小時做了什麼？
第 1 小時：建立專案，安裝 router 和 bootstrap，清除用不到的預設檔案
![](https://i.imgur.com/OOKE0f7.png)

第 2 小時：製作購物車頁面 footer
![](https://i.imgur.com/jWnAB1Y.png)

第 3 小時：製作購物車頁面 footer，嘗試加入 Font Awesome 的 icon
![](https://i.imgur.com/pD1A0YR.png)

第 4 小時：製作購物車頁面 footer，嘗試排版
![](https://i.imgur.com/EKBTK8b.png)

第 5 小時：觀摩其他人已繳交的作業後，發現不必刻最上方的 menu 和最下方的 footer。開始刻購物車的進度條
![](https://i.imgur.com/ay4jHCB.png)

第 6 小時：刻寄送地址表單。
![](https://i.imgur.com/Yu2WmBB.png)

第 7 小時：寄送地址表單完成 v-model 綁定
![](https://i.imgur.com/ZeHnKwu.png)

第 8 小時：寄送地址表單送出後儲存至 local storage。開始刻購物籃
![](https://i.imgur.com/JVgeQY5.png)

第 9 小時：刻購物籃
![](https://i.imgur.com/QxDqJVD.png)

第 10 小時：刻購物籃
![](https://i.imgur.com/u2REmwy.png)

第 11 小時：畫面樣式微調。設定購物籃中，商品數量和小計的連動關係
![](https://i.imgur.com/sahJJUG.png)

第 12 小時：購物籃樣式微調。刻運送方式畫面
![](https://i.imgur.com/XDZZihC.png)

第 13 小時：改成將資料從父元件傳遞到子元件。刻運送方式畫面
![](https://i.imgur.com/NqpGrgw.png)

第 14 小時：點擊「下一步」送出寄送地址後，畫面不需重新整理，就能進到運送方式頁面
![](https://i.imgur.com/mrwj0yK.png)

第 15 小時：一選擇運送方式，購物籃的運費和小計就會更新。實作下一步和上一步功能。
![](https://i.imgur.com/BTquxC4.png)

第 16 小時：使用者從「運送方式」回到「寄送地址」後，看得到剛剛填入的資料。重新命名變數（例如把 stepOne 改成 stepAddress），以增加易讀性。
![](https://i.imgur.com/Azqg5Ji.png)

#### 為了完成這份作業，我查詢了這些課外資料
前情提要：在寫這份作業前，前端關於的 Vue 的課程，我只有用 1.5 倍速看完下列單元的影片：
1. S5 SPA 專案實戰：餐廳論壇，和
2. S6 SPA 專案實戰：串接後端 API 中「串接 API - 登入篇」的某幾個單元

有跟著教案實際操作的，只有 U89 ~ U99 這幾個單元。大概是在這樣的知識前提下寫這份作業。所以我也不太能分辨出「課外資料」和「我沒看過的課內資料」

- 為了加入 Awesome 的 icon，查了 vue-fontawesome 套件。link：https://www.npmjs.com/package/@fortawesome/vue-fontawesome
  不過使用套件失敗了，只有示範用的 fontawesome icon 有出現，footer 中的社群網站 icon 都沒出現。最後改成直接下載 icon 的 svg 圖檔，存到 vue 的 public 資料夾取用 icon
- 為了刻進度條的數字圈圈，搜尋「css 數字圓圈」，link：https://blog.csdn.net/waa_0618/article/details/80743328
- 為了用 v-for 產生下拉選單，搜尋「vue v-for select option」，link：https://ithelp.ithome.com.tw/articles/10198927
- 我想綁定 div 標籤中的文字內容，但 v-model 能綁定的對象不包括 div，搜尋「vue div v-model」，link：https://hsuchihting.github.io/vue-js/20200419/2954354756/
- 我想在 componemt 上註冊點擊事件的監聽器，但 @click 沒有起作用，搜尋「@click component」，link：https://stackoverflow.com/questions/41475447/vue-v-onclick-does-not-work-on-component

#### 這份作業規格說明 / 引導夠清楚，讓我能明白要達成的目標
是

#### 完成這份作業後，我感覺最有挑戰的地方在於？
對 CSS 不熟練、CSS 的命名、commit 的粒度。

#### 其他意見 / 想說的話
新發現：我原本以為不同的 view 或 component，他們的 CSS 設定是，只有父元件的 CSS 設定會影響到子元件的 CSS 的設定，平行元件之間的 CSS 設定各自獨立互不干擾。後來發現似乎不是這樣。

對 figma 不熟。雖然教案裡有提到，figma 裡面有寫 CSS 的設定，但是一開始找不到要去哪裡看 CSS 的設定。因為我一開始誤以為 footer 也要刻，我在 footer 上用滑鼠點了老半天，不管點到哪個元素，右邊欄永遠只有 background 的設定（如下圖右上角紅框）：
![](https://i.imgur.com/fHXpVnz.png)
然後我就以為，不管點任何元件，我都只看得到背景色的 CSS 設定之類的，所以有一陣子我只好瞎猜色碼跟字體大小等等設定。過了好一陣子才發現，原來在左邊的選單列，可以展開選單去找特定元素的 CSS 設定，然後把瞎猜的部分改掉（如果早點發現就不用做兩次工了 XD）。
