<template>
  <div class="icons">
    <swiper :options="swiperOption">
      <swiper-slide v-for="(page, index) of pages" :key="index">
        <div class="icon"
             v-for="item of page"
             :key="item.id">
          <div class="icon-img">
            <img class="icon-img-detail" :src="item.imgUrl" />
          </div>
          <p class="icon-img-info">{{item.imgInfo}}</p>
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeIcon',
  props: {
    iconList: Array
  },
  data() {
    return{
      swiperOption: {
        autoplay: false
      }
    }
  },
  computed:{
    pages() {
      const pages = [];
      this.iconList.forEach((item,index) => {
        const page = Math.floor(index / 8);
        if(!pages[page]){
          pages[page] = []
        }
        pages[page].push(item)
      });
      return pages
    }
  }
}
</script>

<style lang="scss" scoped type="text/scss">
  @import "~styles/_varibles";
  .icons /deep/ .swiper-container{
    height: 0;
    padding-bottom: 50%;
  }
  .icons{
    margin-top: .1rem;
    .icon{
      position: relative;
      overflow: hidden;
      float: left;
      width: 25%;
      padding-bottom: 25%;
      .icon-img{
        position: absolute;
        top: 0;
        bottom: 0.44rem;
        left: 0;
        right: 0;
        box-sizing: border-box;
        padding-bottom: 0.1rem;
        .icon-img-detail{
          display: block;
          margin: 0 auto;
          height: 100%;
        }
      }
      .icon-img-info{
        position: absolute;
        bottom: 0;
        left: 0;
        right: 0;
        height: .44rem;
        line-height: .44rem;
        color: $darkTextColor;
        text-align: center;
        @include ellipsis;
      }
    }
  }
</style>
