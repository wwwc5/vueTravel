<template>
  <div>
    <div class="title">周末去哪儿</div>
    <ul>
      <li class="item border-bottom"
          v-for="item of weekendList"
          :key="item.id">
        <div class="item-img-wrapper">
          <img class="item-img" :src="item.imgUrl"/>
        </div>
        <div class="item-detail">
          <p class="item-title">{{item.title}}</p>
          <p class="item-info">{{item.info}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeWeekend',
  props: {
    weekendList: Array
  }
}
</script>

<style lang="scss" scoped type="text/scss">
  @import "~styles/_varibles";
  .title{
    line-height: .8rem;
    background-color: #eeeeee;
    text-indent: .2rem;
    margin-top: .2rem;
  }
  .item-img-wrapper{
    overflow: hidden;
    height: 0;
    padding-bottom: 37%;
    .item-img{
      width: 100%;
    }
  }
  .item-detail{
    padding: .1rem;
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
  }
</style>
