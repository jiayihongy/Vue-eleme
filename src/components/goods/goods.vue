<template>
  <div class="goods">
    <div class="hot-sell">
      <ul v-for="good in goods">
        <li>{{good.name}}</li>
      </ul>
    </div>
    <div class="goods-details">

    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'goods',
  data () {
    return {
      goods:[]
    }
  },
  created(){
    axios.get('/api/goods')
    .then(res=>{
      this.goods=res.data.data;
      console.log(this.goods)
    })
    .catch(err => {
      alert('获取商品数据失败');
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
