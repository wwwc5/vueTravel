<template>
  <div>
    <div class="title">热销推荐</div>
    <ul>
      <router-link tag="li"
                   class="item border-bottom"
                   v-for="item of recommendList"
                   :key="item.id"
                   :to="'/detail/' + item.id">
        <img class="item-img" :src="item.imgUrl"/>
        <div class="item-detail">
          <p class="item-title">{{item.title}}</p>
          <p class="item-info">{{item.info}}</p>
          <button class="item-button">查看详情</button>
        </div>
      </router-link>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  props: {
    recommendList: Array
  }
}
</script>

<style lang="scss" scoped type="text/scss">
  @import "~styles/_varibles";
  .title{
    line-height: .8rem;
    background-color: #eeeeee;
    text-indent: .2rem;
  }
  .item{
    display: flex;
    height: 1.9rem;
    overflow: hidden;
    .item-img{
      width: 1.7rem;
      height: 1.7rem;
      padding: .1rem;
    }
    .item-detail{
      flex: 1;
      padding: .1rem;
      min-width: 0;
      .item-title{
        line-height: .54rem;
        font-size: .32rem;
        @include ellipsis;
      }
      .item-info{
        line-height: .4rem;
        color: #cccccc;
        @include ellipsis;
      }
      .item-button{
        line-height: .44rem;
        margin-top: .16rem;
        background-color: #ff9300;
        padding: 0 .2rem;
        border-radius: .06rem;
        color: #ffffff;
      }
    }
  }
</style>
