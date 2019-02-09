<template>
  <div class="header">
    <div class="header-left">
      <span class="iconfont left-icon">&#xe624;</span>
    </div>
    <div class="header-middle">
      <span class="iconfont">&#xe632;</span>
      输入城市/景点/游玩主题
    </div>
    <router-link to="/city">
    <div class="header-right">{{this.city}}
      <span class="iconfont right-icon">&#xe64a;</span>
    </div>
    </router-link>
  </div>
</template>

<script>
import { mapState} from'vuex'
export default {
  name: "HomeHeader",
  computed:{
    ...mapState(['city'])
  }
    }
</script>

<style lang="stylus" scoped>
 @import '~styles/varibles.styl'
.header
  display: flex
  line-height: .86rem
  background: $bgColor
  color: #fff
  .header-left
        width: .64rem
        float: left
    .left-icon
        text-align: center
        font-size: .4rem
  .header-middle
    flex: 1
    height: .64rem
    line-height: .6rem
    margin-top: .18rem
    margin-left: .2rem
    padding-left: .2rem
    background: #fff
    border-radius: .1rem
    color: #ccc
  .header-right
    min-width: 1.24rem
    padding: .1rem
    float: right
    text-align: center
    color: #fff
   .right-icon
    font-size: .24rem
    margin-left: -.04rem
</style>
