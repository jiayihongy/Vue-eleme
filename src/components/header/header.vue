<template>
  <div class="elme-header">
    <div class="main">
      <div class="brand-img">
        <img :src="seller.avatar">
      </div>
      <div class="brand-details">
        <div class="title">
          <span></span>
          <span>{{seller.name}}</span>
        </div>
        <div class="description">
          <span>{{seller.description}}/{{seller.deliveryTime}}分钟后送达</span>
        </div>
        <div class="manjian">
          <span :class="tipLog[seller.supports[0].type]"></span>
          <span>{{seller.supports[0].description}}</span>
        </div>
      </div>
      <div class="right-count" @click="popOut = true">
        <span>{{seller.supports.length}}个</span>
        <span class="iconfont icon-xiangyoujiantou"></span>
      </div>
    </div>
    <div class="notice">
      <span></span>
      <span>{{seller.bulletin}}</span>
      <span class="iconfont icon-xiangyoujiantou"></span>
    </div>
    <div class="background">
      <img :src="seller.avatar">
    </div>
    <transition name="fade">
      <div class="pop-out" v-show="popOut" @click="popOut = !popOut">
        <div class="pop-wrap clearfix">
          <div class="pop-main">
            <div class="pop-top">
              <span>{{seller.name}}</span>
              <div class="starts">

              </div>
            </div>
            <div class="pop-middle">

            </div>
            <div class="pop-bottom">

            </div>
          </div>
        </div>
        <div class="pop-footer">
          <span class="iconfont icon-cuowu"></span>
        </div>
      </div>
   </transition>
  </div>
</template>

<script>
  import axios from 'axios'
  export default {
    name: 'header',
    data () {
      return {
          seller:{},
          tipLog:[],
          popOut:false
      }
    },
    created() {
      //获取卖家数据
      axios.get('/api/seller')
    .then(res=>{
      this.seller = res.data.data;
      console.log(res.data.data);
    })
    .catch(err=>{
      alert('狗屁不通!')
    });
    //初始化小图标类名
    this.tipLog = ['jian','zhe','te','piao','bao']
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "../../commen/css/all.scss";
//定义小图标数组
.jian{
  @include bg-img(decrease_2);
}
.zhe{
  @include bg-img(discount_2);
}
.bao{
  @include bg-img(guarantee_2);
}
.piao{
  @include bg-img(invoice_2);
}
.te{
  @include bg-img(special_2);
}
.elme-header {
  background-color: rgba(7, 17, 27, .5);
  font-size: 10px;
  color:#fff;
  position: relative;
  .main{
    display: flex;
    padding: 24px 12px 18px 24px;
    align-items: center;
    position: relative;
    .brand-img{
      img{
        width: 64px;
        height: 64px;
        border-radius: 4px;
      }
    }
    .brand-details{
      margin-left: 16px;
      .title{
        font-size: 0;
        margin-top: 4px;
        span:first-child{
          display: inline-block;
          width: 30px;
          height: 18px;
          @include bg-img(brand);
          background-size: cover;
          background-repeat: no-repeat;
          vertical-align: middle;
        }
        span:last-child{
          font:bold 16px/18px "微软雅黑";
          vertical-align: middle;
          padding-left: 6px;
        }
      }
      .description{
        margin-top: 8px;
        span{
          font-weight:200;
          font-size: 12px;
          line-height: 12px;
        }
      }
      .manjian{
        margin-top: 10px;
        margin-bottom: 4px;
        font-size: 0;
        span:first-child{
          display: inline-block;
          width: 12px;
          height: 12px;
          background-size: cover;
          background-repeat: no-repeat;
          vertical-align: middle;
        }
        span:last-child{
          padding-left: 4px;
          font-size: 10px;
          font-weight: 200;
          line-height: 12px;
          vertical-align: middle;
        }
      }
    }
    .right-count{
      position: absolute;
      right: 12px;
      bottom:16px;
      padding: 7px 8px;
      background-color: rgba(0, 0, 0, .2);
      border-radius: 30px;
      font-size: 0;
      span:first-child{
        font-size: 10px;
        font-weight: 200;
        line-height: 12px;
      }
      span.iconfont{
        font-size: 6px;
        font-weight: bold;
        padding-left: 4px;
      }
    }
  }
  .notice{
    position: relative;
    height: 28px;
    line-height: 28px;
    padding: 0 22px 0 12px;
    background-color: rgba(7, 17, 27, .2);
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
    span:first-child{
      display: inline-block;
      width: 22px;
      height: 12px;
      @include bg-img(bulletin);
      background-size: cover;
      margin-top: 7px;
      vertical-align: top;
    }
    span:nth-child(2){
      padding: 0 4px;
      vertical-align: top;
    }
    span:last-child{
      position: absolute;
      top: 8;
      right: 12px;
      font-size: 10px;
    }
  }
  .background{
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    overflow:hidden;
    z-index: -1;
    filter: blur(10px);
    img{
      width: 100%;
    }
  }
  .pop-out{
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(7, 17, 27, .8);
    z-index: 10;
    backdrop-filter: blur(10px);
    &.fade-enter{
      opacity: 0;
      transform: scaleX(0.1) scaleY(0.1);
    }
    &.fade-leave{
      opacity: 1;
      transform: scaleX(1) scaleY(1);
    }
    &.fade-enter-active{
      transition: all .5s;
    }
    &.fade-leave-active{
      transform: scaleX(0.1) scaleY(0.1);
      opacity: 0;
      transition: all .5s;
    }
    .pop-wrap{
      width: 100%;
      min-height: 100%;
      .pop-main{
        height: 100%;
        padding-top: 64px;
        padding-bottom: 64px;
      }
    }
    .pop-footer{
      width: 32px;
      height: 32px;
      margin: -64px auto 0 auto;
      clear: both;
      &>.iconfont{
        font-size: 32px;
      }
    }
  }
}
</style>
