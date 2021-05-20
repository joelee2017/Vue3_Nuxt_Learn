# Vue3_Nuxt_Learn
Vue3_Nuxt_SSR_學習

[TOC]

------

### Vue 進階篇 - Nuxt 架構解析-static&assets

- static  - 不需要經過nuxt打包編譯的檔案放此處

  ico、音樂、壓縮zip

- assets - 只要經過nuxt打包編譯的檔案放此處

  圖片、css、第三方檔案

------

### Vue 進階篇 - Nuxt 架構解析-store&plugins&middleware

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

### Vue 進階篇 - Nuxt 生命週期表 Nuxt Lifecycle

https://nuxtjs.org/docs/2.x/concepts/nuxt-lifecycle

Nuxt  因為會有server端的關係，所以會跟原生的vue 生命週期有差異。

![understanding-nuxt-2-12-lifecycle-hooks](https://nuxtjs.org/docs/2.x/nuxt-lifecycle.svg)

------

### Vue 進階篇 - Nuxt 生命週期-asyncData與Data

為執行階段會提供的生點週期函式，網頁在被render到網頁之前，在server端執行的生命週期。

要做非同步處理，取api資料時，要做seo，就能在asyncData中去打api打內容render出來

asyncData在生命週期中只會執行一次。

asyncData只會執行一次的關係，所以無法被vue其它功能所捕獲。

asyncData中的內容，還要給程式其它內容使用的話，才會在data中命名一樣的物件。

asyncData會覆寫data一樣名稱的內容。

------

### Vue 進階篇 - GET API SSR實作

若資料是必需在進到頁面前就拿到並渲染到畫面就必需在 asyncData在生命週期中執行，非同步執行。

```js
 async asyncData() {
    const res = await axios.get('https://vue-lessons-api.herokuapp.com/photo/list');
    // console.log(res);
    return{
      res: res.data
    };
  },
```

------

### Vue 進階篇 - asyncData重要事項

- asyncData 只有在pages資料夾下的檔案才會執行，其它不會被執行。
- 因為 asyncData  是指頁面渲染以前， server 去執行的動作。
- components 、 layouts 是沒有 asyncData   的。
- asyncData  有某些js 是不能使用的，譬 alert。
- server 端在執行的時侯頁面還沒被建構出來故無法使用。
- document、windows、this 都無法使用。
- asyncData   時vue實體尚未被建構出故無法使用 this 。

------

### Vue 進階篇 - Nuxt 生命週期-fetch

-  asyncData  跟 fetch 都是在 server 端執行的。
- 相較於 asyncData 只有在pages資料夾下的檔案才會執行 ，fetch 都可以執行。
- fetch 是可以取得 this ，因為在生命週期 created 時vue實體就已經被建構了。
- fetch 無法使用 return， 但可以使用覆寫。

![image-20210517215046998](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210517215046998.png)

------

### Vue 進階篇 - fetch的狀態處理-1

改用 fetch  來取 api 資料

------

### Vue 進階篇 - fetch的狀態處理-2

```js
export default {
  fetchOnServer: false
}
```

- 如果把 fetchOnServer 設定成 false，那這樣fetch 就只會在 client 端被執行。
- 等同於server 拿完資料，在讓 client 去執行渲染。

------

### Vue 進階篇 - fetch的狀態處理-3

Fetch 提供的參數

- $fetchState.pending ( true  |  false ) :  讓你在 client 端去判斷 API 載入完成沒有

  ```vue
    <h1 v-if="$fetchState.pending">Loading...</h1>
  打資料時true ，回資料後false
  ```

- $fetchState.error ( null  |  { } ) : 當發生畫面上的內容發生錯誤的時候，去判斷錯誤的部分

  ```vue
    <h1 v-if="$fetchState.error">ERROR {{$fetchState.error }}</h1>
  ```

- $fetchState.timestamp (  Integer  ) : 顯示最後一次非同步處理的時間 



------













