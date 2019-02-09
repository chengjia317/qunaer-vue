<template>
  <div>
    <div class="list" v-for="(item,index) of list" :key="index">
      <div class="list-title border-bottom">
        <span class="list-title-icon"></span>
        {{item.title}}
      </div>
      <div v-if="item.children" class="item-children">
        <detail-list :list="item.children"> </detail-list>
      </div>

    </div>
  </div>

</template>

<script>
export default {
  name: "DetailList",
  props:{
    list:Array
  }
}
</script>

<style lang="stylus" scoped>
.list-title
  line-height:.86rem
  font-size: .32rem
  padding: 0 .2rem
.list-title-icon
  display: inline-block
  width: .36rem
  height: .36rem
  position: relative
  top: .06rem
  left:.06rem
  background: url(http://s.qunarzz.com/piao/image/touch/sight/detail.png) 0 -.45rem no-repeat
  margin-right: .1rem
  background-size: .4rem 3rem
.item-children
  padding: 0 .2rem
</style>
