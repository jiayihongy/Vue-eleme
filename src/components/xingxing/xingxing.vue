<template>
  <div class="xingxing" :class="starType">
    <span v-for="(val,index) in statFactroy" :class="val"></span>
  </div>
</template>

<script>
export default {
  name: 'xingxing',
  props:{
    size:0,
    score:0
  },
  computed:{
    starType(){
      return 'xingxing'+this.size;
    },
    statFactroy(){
      var arr = [];
      const on = 'on';
      const half = 'half';
      const none = 'none';
      const LENGTH = 5;
      var score = Math.floor(this.score*2)/2;
      var feizheng = score % 1 !== 0;
      var zheng = Math.floor(score);
      for(let i = 0;i < zheng;i++){
        arr.push(on);
      }
      if(feizheng){
        arr.push(half);
      }
      while (arr.length < LENGTH) {
        arr.push(none);
      }
      return arr;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "../../commen/css/all.scss";
  .xingxing{
    font-size: 0;
    &.xingxing24{
      span{
        display: inline-block;
        width: 10px;
        height: 10px;
        margin-right: 3px;
        background-size: cover;
        background-repeat: no-repeat;
        &:last-child{
          margin: 0
        }
      }
      &>.none{
        @include bg-img(star24_off);
      }
      &>.half{
        @include bg-img(star24_half);
      }
      &>.on{
        @include bg-img(star24_on);
      }
    }
    &.xingxing36{
      span{
        display: inline-block;
        width: 15px;
        height: 15px;
        margin-right: 6px;
        background-size: cover;
        background-repeat: no-repeat;
        &:last-child{
          margin: 0
        }
      }
      &>.none{
        @include bg-img(star36_off);
      }
      &>.half{
        @include bg-img(star36_half);
      }
      &>.on{
        @include bg-img(star36_on);
      }
    }
    &.xingxing48{
      span{
        display: inline-block;
        width: 20px;
        height: 20px;
        margin-right: 22px;
        background-size: cover;
        background-repeat: no-repeat;
        &:last-child{
          margin: 0
        }
      }
      &>.none{
        @include bg-img(star48_off);
      }
      &>.half{
        @include bg-img(star48_half);
      }
      &>.on{
        @include bg-img(star48_on);
      }
    }
  }
</style>
