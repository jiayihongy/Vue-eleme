<template>
  <div id="app">
    <elmeHeader></elmeHeader>
    <section class="leader border">
      <span><router-link to="/goods">商品</router-link></span>
      <span><router-link to="/ratings">评价</router-link></span>
      <span><router-link to="/seller">商家</router-link></span>
    </section>
    <section class="main">
      <router-view></router-view>
    </section>
    <footer>
      我是最下面
    </footer>
  </div>
</template>

<script>
import elmeHeader from '@/components/header/header'
export default {
  name: 'app',
  components:{elmeHeader}
}
</script>

<style lang="scss">
  @import "commen/css/all";
#app {
  text-align: center;
  .leader{
    display: flex;
    height: 80px;
    line-height: 80px;
    border-bottom: 1px solid rgba(7,17,27,0.8);
    span{
      flex:1;
      font-size: 28px;
      a{
        color: #4d555d;
        &:hover{
          color:#f01414;
        }
      }
    }
  }
}
</style>
