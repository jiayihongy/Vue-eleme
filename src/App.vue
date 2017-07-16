<template>
  <div id="app">
    <elmeHeader></elmeHeader>
    <section class="leader">
      <span>商品</span>
      <span>评价</span>
      <span>什么</span>
    </section>
    <section class="main">
      我才是主体
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
#app {
  text-align: center;
  .leader{
    display: flex;
    span{
      flex:1;
    }
  }
}
</style>
