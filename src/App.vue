<template>
  <div id="app">
    <my-header title="tabBar"></my-header>
    <component :is="componentName"></component>
    <my-footer :tabList="tabList" @change-component="componentName = $event"></my-footer>
  </div>
</template>
<script>
import MyFooter from './components/MyFooter.vue'
import MyHeader from './components/MyHeader.vue'
import MyGoodsList from '@/views/MyGoodsList'
import MyGoodsSearch from '@/views/MyGoodsSearch'
import MyUserInfo from '@/views/MyUserInfo'

export default {
  components: {
    MyHeader,
    MyFooter,
    MyUserInfo,
    MyGoodsSearch,
    MyGoodsList
  },
  data() {
    return {
      componentName: 'MyGoodsList',
      tabList: [
        {
          iconText: 'icon-shangpinliebiao',
          text: '商品列表',
          componentName: 'MyGoodsList'
        },
        {
          iconText: 'icon-sousuo',
          text: '商品搜索',
          componentName: 'MyGoodsSearch'
        },
        {
          iconText: 'icon-user',
          text: '我的信息',
          componentName: 'MyUserInfo'
        }
      ]
    }
  }
}
</script>

<style scoped>
#app {
  padding-top: 50px;
}
</style>
