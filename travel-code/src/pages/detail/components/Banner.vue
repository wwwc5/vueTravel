<template>
  <div>
    <div class="banner" @click="handleBannerClick">
      <img class="banner-img" :src="bannerImage" />
      <div class="banner-info">
        <div class="banner-title">{{this.sightName}}</div>
        <div class="banner-number">
          <span class="iconfont banner-icon">&#xe602;</span>
          {{this.gallaryImages.length}}
        </div>
      </div>
    </div>
    <fade>
      <common-gallary :imgs="gallaryImages"
                      v-show="showGallary"
                      @close="handleGallaryClose">
      </common-gallary>
    </fade>
  </div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary'
import Fade from 'common/fade/Fade'
export default {
  name: 'DetailBanner',
  props: {
    sightName: String,
    bannerImage: String,
    gallaryImages: Array
  },
  data(){
    return{
      showGallary:false
    }
  },
  components:{
    CommonGallary,
    Fade
  },
  methods: {
    handleBannerClick(){
      this.showGallary = true
    },
    handleGallaryClose(){
      this.showGallary = false
    }
  }
}
</script>

<style lang="scss" scoped type="text/scss">
  .banner{
    overflow: hidden;
    height: 0;
    padding-bottom: 55%;
    background-color: #dddddd;
    position: relative;
    .banner-img{
      width: 100%;
    }
    .banner-info{
      display: flex;
      position: absolute;
      bottom: 0;
      right: 0;
      left: 0;
      line-height: .6rem;
      color: #ffffff;
      background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, .8));
      .banner-title{
        flex: 1;
        font-size: .32rem;
        padding: 0 .2rem;
      }
      .banner-number{
        margin-top: .14rem;
        padding: 0 .4rem;
        line-height: .32rem;
        height: .32rem;
        border-radius: .2rem;
        font-size: .24rem;
        background-color: rgba(0, 0, 0, .8);
        .banner-icon{
          font-size: .24rem;
        }
      }
    }
  }
</style>
