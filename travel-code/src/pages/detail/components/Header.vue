<template>
  <div>
    <router-link tag="div"
                 to="/"
                 class="header-abs"
                 v-show="showAbs">
      <div class="iconfont back-icon">&#xe624;</div>
    </router-link>
    <div class="header-fixed"
         v-show="!showAbs"
         :style="opacityStyle">
      <router-link to="/">
        <div class="iconfont header-fixed-back">&#xe624;</div>
      </router-link>
      景点详情
    </div>
  </div>
</template>

<script>
  export default {
    name: 'DetailHeader',
    data() {
      return{
        showAbs: true,
        opacityStyle: {
          opacity: 0
        }
      }
    },
    methods:{
      handleScroll() {
        const top = document.documentElement.scrollTop;
        if(top > 60){
          let opacity = top / 140;
          opacity = opacity > 1? 1 : opacity;
          this.opacityStyle = { opacity };
          this.showAbs = false
        } else {
          this.showAbs = true
        }
      }
    },
    mounted(){
      window.addEventListener('scroll', this.handleScroll)
    },
    unmounter() {
      window.removeEventListener('scroll', this.handleScroll)
    }
  }
</script>

<style lang="scss" scoped type="text/scss">
  @import '~styles/_varibles.scss';
  .header-abs{
    position: absolute;
    left: .2rem;
    top: .2rem;
    width: .8rem;
    height: .8rem;
    line-height: .8rem;
    border-radius: .4rem;
    background-color: rgba(0, 0, 0, .8);
    text-align: center;
    .back-icon{
      color: white;
      font-size: .4rem;
    }
  }
  .header-fixed {
    position: fixed;
    top: 0;
    right: 0;
    left: 0;
    height: .86rem;
    line-height: .86rem;
    text-align: center;
    color: #ffffff;
    background-color: $bg-color;
    font-size: .32rem;
    z-index: 2;
    .header-fixed-back{
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
