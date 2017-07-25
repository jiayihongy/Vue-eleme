<template>
  <div class="goods">
    <div class="hot-sell">
      <ul v-for="good in goods">
        <li>{{good.name}}</li>
      </ul>
    </div>
    <div class="goods-list">
      <div class="goods-details" v-for="good in goods">
        <div>
          <p>{{good.name}}</p>
        </div>
        <ul v-for="food in good.foods">
          <li>
            <div class="goods-img">
              <img :scr="food.icon" style="width:64px;height:64px">
            </div>
            <div class="goods-descripthon">
              <p>{{food.name}}</p>
              <p>{{food.description}}</p>
              <p>
                <span>月售{{food.sellCount}}份</span>
                <span>{{food.rating}}%好评率</span>
              </p>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'goods',
  data () {
    return {
      goods:[],
    }
  },
  created(){
    axios.get('/api/goods')
    .then(res=>{
      // 获取商品对象数组
      this.goods=res.data.data;
    })
    .catch(err => {
      alert('获取商品数据失败');
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "../../commen/css/all.scss";
  .goods{
    display: flex;
    .hot-sell{
      box-sizing: border-box;
      ul{
        li{
          width: 80px;
        }
      }
    }
    .goods-list{

    }
  }
</style>
