<template>
  <div>
    <detail-banner :sightName="sightName"
                   :bannerImage="bannerImage"
                   :gallaryImages="gallaryImages"></detail-banner>
    <detail-header></detail-header>
    <div class="content">
      <detail-list :list="list"></detail-list>
    </div>
  </div>
</template>

<script>
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
import axios from 'axios'
import {PATH} from 'common/axios-test'
export default {
  name: 'Detail',
  components:{
    DetailBanner,
    DetailHeader,
    DetailList
  },
  data() {
    return {
      sightName: '',
      bannerImage: '',
      gallaryImages: [],
      list: []
    }
  },
  methods: {
    getDetailInfo() {
      axios.get(PATH + '/detail.json?id=' + this.$route.params.id).then(this.handleGetDataSucc)
    },
    handleGetDataSucc(res) {
      res = res.data;
      if(res.ret && res.data) {
        const data = res.data;
        this.sightName = data.sightName;
        this.bannerImage = data.bannerImg;
        this.gallaryImages = data.gallaryImgs;
        this.list = data.categoryList
      }
    }
  },
  mounted() {
    this.getDetailInfo()
  }
}
</script>

<style scoped>
  .content{
    height: 50rem;
  }
</style>
