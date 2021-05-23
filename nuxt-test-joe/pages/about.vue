// about頁面，會自動產生route後會在自動渲染(ssr功能)
<script>
export default {
  head() {
    return{
        title: 'about page - ' + this.title,
            meta: [
            {
                hid: 'description',
                name: 'description',
                content: 'about page description'
            }
            ],
        }    
    },
  data(){
      return {
          title:'joe'
      }
  }
}
</script>
<template>
    <div>
        <h1>about</h1>
    </div>
</template>