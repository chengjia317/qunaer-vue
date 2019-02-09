<template>
  <div class="container" @click="handelGallaryClick">
    <div class="wrapper">
      <swiper :options="swiperOption">
        <!-- slides -->
        <swiper-slide v-for="(item,index) in imgs" :key="index">
          <img class="gallary-img" :src=item />
        </swiper-slide>
        <!-- Optional controls -->
        <div class="swiper-pagination"  slot="pagination"></div>
      </swiper>
    </div>
  </div>
</template>

<script>
export default {
  name: "CommonGallary",
  data(){
    return{
      swiperOption:{
        pagination:'.swiper-pagination',
        paginationType:'fraction',
        observer:true,
        observeParents:true
      }
    }
  },
  props:{
    imgs:Array
  },
  methods:{
    handelGallaryClick(){
      this.$emit('close')
    }
  }
}
</script>

<style lang="stylus" scoped>
.container>>>.swiper-container
  overflow: inherit
.container
  background: #000
  position: fixed
  top:0
  left:0
  right:0
  bottom:0
  display: flex
  flex-direction: column
  justify-content: center
  z-index:99
.wrapper
  width:100%
  height: 0
  padding-bottom: 100%
.gallary-img
  width: 100%
.swiper-pagination
  bottom: -1rem
  color:#fff
</style>
