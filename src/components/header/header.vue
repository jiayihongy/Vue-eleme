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
            <p>离开教室里的咖啡机</p>
            <p>离开教室里的咖啡机</p>
            <p>离开教室里的咖啡机</p>
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
      console.log(res.data);
    })
    .catch(err=>{
      alert('狗屁不通!')
    });
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .elme-header {
    height: 134px;
    overflow: hidden;
    background-color: #7e8c8d;
    position: relative;
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
      }
    }
    .notice{
      height: 28px;
      width: 100%;
      background-color: yellow;
      position: absolute;
      bottom: 0;
      left: 0;
      z-index: 10;
    }
  }
</style>
