<template>
  <div class="container" @click="handleGallaryClick">
    <div class="wrapper">
      <swiper :options="swiperOptions">
        <swiper-slide v-for="(item, index) of imgs" :key="index">
          <img class="gallary-img" :src="item">
        </swiper-slide>
      </swiper>
      <div class="swiper-pagination" slot="pagination"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CommonGallary',
  props:{
    imgs:{
      type: Array,
      default(){
        return []
      }
    }
  },
  data(){
    return{
      swiperOptions:{
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        observeParents: true,
        observer: true
      }
    }
  },
  methods:{
    handleGallaryClick(){
      this.$emit("close")
    }
  }
}
</script>

<style lang="scss" scoped type="text/scss">
  .container{
    display: flex;
    flex-direction: column;
    justify-content: center;
    position: fixed;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    background-color: black;
    z-index: 99;
    .wrapper{
      height: 0;
      width: 100%;
      padding-bottom: 100%;
      .gallary-img{
        width: 100%;
      }
      .swiper-pagination{
        color: white;
      }
    }
  }
</style>
