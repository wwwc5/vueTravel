<template>
  <div class="wrapper">
    <swiper :options="swiperOption" v-if="showSwiper">
      <!-- slides -->
        <swiper-slide v-for="item of swiperList" :key="item.id">
          <img class="swiper-img" :src="item.imgUrl">
        </swiper-slide>
      <!-- Optional controls -->
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  props: {
    swiperList: Array
  },
  data() {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true
      }
    }
  },
  computed: {
    showSwiper() {
      return this.swiperList.length
    }
  }
}
</script>

<style lang="scss" scoped type="text/scss">
  .wrapper /deep/ .swiper-pagination-bullet-active{
    background: #ffffff !important
  }
  .wrapper{
    overflow: hidden;
    width: 100%;
    height: 0;
    padding-bottom: 26.67%;
    background-color: #dddddd;
    .swiper-img{
      width: 100%;
    }
  }
</style>
