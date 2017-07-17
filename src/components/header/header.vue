<template>
  <div class="elme-header">
    <div class="header-shadom">
      <img :src="seller.avatar">
    </div>
    <div class="header-main">
        <div class="brand-img">
          <img :src="seller.avatar" alt="">
        </div>
        <div class="brand-details">
            <div class="brand-title">
              <i></i>
              <span>{{seller.name}}</span>
            </div>
            <div class="brand-description">
              <span>{{seller.description}}/{{seller.deliveryTime}}分钟后送达</span>
            </div>
            <div class="manjian" v-if="seller.supports">
              <i></i>
              <span>{{seller.supports[0].description}}</span>
            </div>
            <div class="baba">
              <span>5</span>
              <span>&gt;</span>
            </div>
        </div>
    </div>
    <div class="notice">

    </div>
  </div>
</template>

<script>
  import axios from 'axios'
  export default {
    name: 'header',
    data () {
      return {
          seller:{}
      }
    },
    created() {
      axios.get('/api/seller')
    .then(res=>{
      this.seller = res.data.data;
      console.log(res.data.data);
    })
    .catch(err=>{
      alert('狗屁不通!')
    });
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "../../commen/css/all.scss";
  .elme-header {
    height: 134px;
    overflow: hidden;
    background-color: #7e8c8d;
    position: relative;
    text-align: left;
    .header-shadom{
      width: 100%;
      height: 100%;
      overflow: hidden;
      img{
        width: 100%;
      }
    }
    .header-main {
      height: 106px;
      width: 100%;
      background-color:rgba(7,17,27,0.8);
      padding: 24px 12px 18px 24px;
      position: absolute;
      top: 0;
      left: 0;
      z-index: 10;
      color: #fff;
      .brand-img{
        float: left;
        img{
          height: 64px;
          width: 64px;
          border-radius: 5px;
        }
      }
      .brand-details{
        float: left;
        padding-left: 12px;
        .brand-title{
          font-size: 0;
          i{
            display: inline-block;
            width: 30px;
            height: 18px;
            @include bg-img(brand);
            background-size: cover;
            background-repeat: no-repeat;
            vertical-align: middle;
          }
          span{
            font: bold 16px/18px "微软雅黑";
            vertical-align: middle;
            padding-left: 6px;
          }
        }
        .brand-description{
          font-size: 0;
          padding-top: 8px;
          padding-bottom: 10px;
          span{
            display: inline-block;
            font-size: 12px;
            font-weight: 200;
            line-height: 12px;
          }
        }
        .manjian{
          font-size: 0;
          i{
            display: inline-block;
            width: 12px;
            height: 12px;
          }
          span{
            display: inline-block;
            font-size: 10px;
            line-height: 10px;
          }
        }
      }
    }
    .notice{
      height: 28px;
      width: 100%;
      background-color: rgba(7,17,27,0.2);
      position: absolute;
      bottom: 0;
      left: 0;
      z-index: 10;
    }
  }
</style>
