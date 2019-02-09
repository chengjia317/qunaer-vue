<template>
  <div>
    <div class="search">
      <input v-model="keywords" class="search-input" type="text" placeholder="输入城市名或拼音">
    </div>
    <!--有搜索数据才显示-->
    <div class="search-content" ref="search" v-show="keywords" >
      <ul>
        <li v-for="item of list" class="search-item border-bottom" :key="item.id" @click="handleCityClick(item.name)">{{item.name}}</li>
        <li class="search-item border-bottom" v-show="hasNoData">没有找到搜索结果</li>
      </ul>
    </div>
  </div>
</template>

<script>
  import Bscroll from 'better-scroll'
  import { mapMutations } from 'vuex'
export default {
  name: "CitySearch",
  props:{
    cities:Object
  },
  data(){
    return{
      keywords:'',
      timer:null,
      list:[]
    }
  },
  computed:{
    hasNoData(){
      //没有没有找到数据就显示
      return !this.list.length;
    }
  },
  methods:{
    handleCityClick(city){
      this.changeCity(city)
      this.$router.push('./')
    },
    ...mapMutations(['changeCity'])
  },
  watch:{
    keywords(){
      if(this.timer){
        clearTimeout(this.timer);
      }
      if(!this.keywords){
        this.list='';
        return this.list;
      }
      this.timer=setTimeout(()=>{
        const result=[];
        for(let i in this.cities){
          this.cities[i].forEach((value)=>{
            if(value.name.indexOf(this.keywords)>-1||value.spell.indexOf(this.keywords)>-1){
              result.push(value);
            }
          })
        }
        this.list=result;
      },100)

    }
  },
  mounted(){
    this.scroll =new Bscroll(this.$refs.search)//解决不能滑动的问题
  }
}
</script>

<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
.search
  height:.72rem
  background: $bgColor
  padding: 0 .1rem
.search-input
  height: .62rem
  line-height: .62rem
  width: 100%
  text-align: center
  border-radius: .06rem
  color: #666
  padding: 0 .1rem
  box-sizing: border-box
.search-content
  z-index:1
  position: absolute
  background-color: #eee
  top: 1.58rem
  left:0
  overflow: hidden //?
  bottom:0
  right:0
.search-item
  line-height:.62rem
  padding-left:.2rem
  color:#666
  background-color: #fff;
</style>
