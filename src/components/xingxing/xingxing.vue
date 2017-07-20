<template>
  <div class="xingxing">
    <span class="half"></span>
  </div>
</template>

<script>
export default {
  name: 'xingxing',
  data () {
    return {

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "../../commen/css/all.scss";
  .xingxing{
    .none{
      @include bg-img(star24_off);
    }
    .half{
      @include bg-img(star24_half);
    }
    .on{
      @include bg-img(star24_on);
    }
    span{
      display: inline-block;
      width: 10px;
      height: 10px;
      background-size: cover;
      background-repeat: no-repeat;
    }
  }
</style>
