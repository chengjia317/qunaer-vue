<template>
    <div class="icons">
      <swiper :options="swiperOption">
        <swiper-slide v-for="(page,index) of pages" :key="index">
      <div class="icon" v-for="item of page" :key="item.id">
        <div class="icon-box">
          <img class="icon-img" :src="item.imgUrl" />
        </div>
          <p class="icon-word" >{{item.des}}</p>
      </div>
        </swiper-slide>
      </swiper>
    </div>
</template>

<script>
export default {
  name: "HomeIcons",
  props:{
    list:Array
  },
  data(){
    return{
      swiperOption:{
        autoPlay:false
      }
    }
  },
  computed: {
    pages() {
      const pages = []
      this.list.forEach((item, index) => {
        const page = Math.floor(index / 8);
        if (!pages[page]) {
          pages[page] = [];
        }
        pages[page].push(item);
      })
      return pages
    }
  }
    }
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  @import '~styles/mixins.styl'
.icons >>> .swiper-container
  height:0
  padding-bottom: 50%
.icons
  margin-top: .1rem
.icon
  float: left
  width: 25%
  position: relative
  overflow: hidden
  height:0
  padding-bottom: 25%
.icon-box
  position: absolute
  top:0
  left:0
  right:0
  bottom: .44rem
  padding: .1rem
  box-sizing: border-box
.icon-img
  height: 100%
  display: block
  margin: 0 auto
 .icon-word
   position: absolute
   left:0
   right:0
   bottom: 0
   height: .44rem
   line-height: .44rem
   text-align: center
   color:$darkColor
   ellipsis()
</style>
