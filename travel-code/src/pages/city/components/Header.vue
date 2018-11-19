<template>
  <div class="header">
    城市选择
    <router-link to="/">
      <div class="iconfont back-icon">&#xe624;</div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style lang='scss' scoped type="text/scss">
  @import '~styles/_varibles.scss';
  .header{
    position: relative;
    overflow: hidden;
    height: .86rem;
    line-height: .86rem;
    text-align: center;
    color: #ffffff;
    background-color: $bg-color;
    font-size: .32rem;
    .back-icon{
      width: .64rem;
      text-align: center;
      font-size: .4rem;
      position: absolute;
      top: 0;
      left: 0;
      color: white;
    }
  }
</style>
