<template>
  <div>
    <router-link tag="div" to="/" class="header-icon" v-show="showHeader">
      <span class="iconfont">&#xe624;</span>
    </router-link>
    <div class="detail-top" v-show="!showHeader" :style="headerStyle">景点详情
      <router-link to="/">
        <span class="iconfont header-back">&#xe624</span>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "DetailHeader",
  data(){
    return{
      showHeader:true,
      headerStyle:{
        opacity:0
      }
    }
  },
  methods:{
    handleScroll(){
      const disX=document.documentElement.scrollTop;
      if(disX>100){
        let opacity=disX/180;
        opacity>1?1:opacity;
        this.headerStyle={opacity}
        this.showHeader=false
      }else{
        this.showHeader=true
      }
    }
  },
  activated(){
    window.addEventListener('scroll',this.handleScroll)
  },
  deactivated(){
    window.removeEventListener('scroll',this.handleScroll)
  }
    }
</script>

<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
.header-icon
  width:.72rem;
  height .72rem;
  border-radius 50%
  background-color: rgba(0,0,0,0.4)
  text-align: center
  line-height:.72rem;
  color: #fff
  position: absolute
  top: 0.1rem
  left: 0.1rem
  z-index:2
.detail-top
  z-index:2
  width: 100%
  height:.86rem
  background-color: $bgColor
  text-align: center
  line-height:.86rem
  color: #fff
  position: fixed
  top:0
  left:0
  right:0
  font-size: .32rem
.header-back
  position: absolute
  top:0
  left:.1rem
  color: #fff
  font-size: .4rem
</style>
