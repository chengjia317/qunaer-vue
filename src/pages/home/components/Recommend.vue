<template>
  <div>
    <div class="title">热销推荐</div>
    <ul>
      <router-link tag="li" class="item border-bottom" v-for="item of list" :key="item.id" :to="'/detail/'+item.id">
        <img  class="item-img" :src="item.imgUrl" />
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-des">{{item.des}}</p>
          <button class="item-btn">查看详情</button>
        </div>
      </router-link>
    </ul>
  </div>
</template>

<script>
    export default {
      name: "HomeRecommend",
      props:{
          list:Array
      }
    }
</script>

<style  lang="stylus" scoped>
  @import '~styles/mixins.styl'
.title
  line-height: .8rem
  background: #eee
  margin-top:.2rem
  text-indent: .2rem
.item
  display: flex
  flex: 1
  height: 1.9rem
  overflow:hidden
.item-img
  width: 1.7rem
  height: 1.7rem
  padding: .1rem
.item-info
  flex:1
  padding: .1rem
  min-width: 0
.item-title
  line-height: .54rem
  font-size: .32rem
  ellipsis()
 .item-des
   line-height: .4rem
   color: #ccc
   ellipsis()
 .item-btn
   line-height: .44rem
   margin-top: .16rem
   background: #ff9300
   padding: 0 .1rem
   border-radius: .05rem
   color: #fff
</style>
