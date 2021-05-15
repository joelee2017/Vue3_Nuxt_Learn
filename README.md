# Vue3_Nuxt_Learn
Vue3_Nuxt_SSR_學習

------

Vue 進階篇 - Nuxt 架構解析-static&assets

- static  - 不需要經過nuxt打包編譯的檔案放此處

  ico、音樂、壓縮zip

- assets - 只要經過nuxt打包編譯的檔案放此處

  圖片、css、第三方檔案

------

Vue 進階篇 - Nuxt 架構解析-store&plugins&middleware

- middleware 中間層

  驗證、檢查、轉導、共用全局使用的東西

- plugins - nuxt套件資料夾

  執行時會從 nuxt.config.js 中讀取出來

- store - vuex
------

簡報中有完整介紹

assets：需要被打包的資源，例如你的 images 等等
components：頁面的最小單位組件
layouts：頁面共用的版型，例如 header、 footer
middleware：進入頁面前需要做的中間層
pages：頁面放的地方，一個 .vue 就是一個頁面
plugins：自定義的nuxt套件的資料夾
static：靜態資源，不需要被打包的資源
store： Vuex所放的資料夾