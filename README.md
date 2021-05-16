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

------

Vue 進階篇 - Nuxt 生命週期表 Nuxt Lifecycle

https://nuxtjs.org/docs/2.x/concepts/nuxt-lifecycle

Nuxt  因為會有server端的關係，所以會跟原生的vue 生命週期有差異。

![understanding-nuxt-2-12-lifecycle-hooks](https://nuxtjs.org/docs/2.x/nuxt-lifecycle.svg)

------

Vue 進階篇 - asyncData重要事項

為執行階段會提供的生點週期函式，網頁在被render到網頁之前，在server端執行的生命週期。

要做非同步處理，取api資料時，要做seo，就能在asyncData中去打api打內容render出來

asyncData在生命週期中只會執行一次。

asyncData只會執行一次的關係，所以無法被vue其它功能所捕獲。

asyncData中的內容，還要給程式其它內容使用的話，才會在data中命名一樣的物件。

asyncData會覆寫data一樣名稱的內容。

------





