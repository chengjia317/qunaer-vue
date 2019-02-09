<template>
    <div class="header">城市选择
      <router-link to="/">
      <div class="iconfont header-back">&#xe624</div>
      </router-link>
    </div>
</template>

<script>
  export default {
    name: "CityHeader"
    }
</script>

<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
.header
  overflow: hidden
  height: .86rem
  line-height: .86rem
  text-align: center
  background-color: $bgColor;
  color: #fff
  font-size: .32rem
  position: relative
 .header-back
   width: .64rem
   font-size: .4rem
   text-align: center
   position: absolute
   top:0
   left:0
   color: #fff
</style>
