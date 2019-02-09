<template>
  <div>
    <div class="banner" @click="handleGallaryShow">
      <img :src=bannerImg class="banner-img">
      <div class="banner-info">
        <div class="banner-title">{{this.sightName}}</div>
        <div class="banner-number">
          <span class="iconfont banner-icon">&#xe692;</span>
          {{this.gallaryImgs.length}}
        </div>
      </div>
    </div>
    <fade-animation>
     <common-gallary :imgs="gallaryImgs" v-show="showGallary" @close="handleGallaryClose"> </common-gallary>
    </fade-animation>
  </div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary'
import FadeAnimation from 'common/fade/FadeAnimation'

export default {
  name: "DetailBanner",
  components:{
    CommonGallary,
    FadeAnimation
  },
  props:{
    sightName:String,
    bannerImg:String,
    gallaryImgs:Array
  },
  data(){
    return{
      showGallary:false
    }
  },
  methods:{
    handleGallaryShow(){
      this.showGallary=true;
    },
    handleGallaryClose(){
      this.showGallary=false;
    }
  }
}
</script>

<style lang="stylus" scoped>
.banner
  position: relative
  overflow: hidden
  height:0
  padding-bottom:54%
.banner-img
  width:100%
.banner-info
  position: absolute
  left:0
  bottom:0
  right:0
  display: flex
  line-height:.6rem
  color: #fff
  background-image: linear-gradient(top, rgba(0 ,0, 0, 0), rgba(0, 0, 0, 0.8))
.banner-title
  flex: 1
  padding: 0 .2rem
  font-size:.32rem
.banner-number
  line-height: .4rem
  padding:0 .4rem
  margin-top:.14rem
  height:.4rem
  border-radius:.2rem
  font-size: .24rem
  background-color: rgba(0,0,0,.8);
.banner-icon
  font-size:.24rem

</style>
