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
  .leader{
    display: flex;
    height: 40px;
    line-height: 40px;
    text-align: center;
    @include border-1px(rgba(7,17,27,0.2));
    span{
      flex:1;
      font-size: 14px;
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
