<template>
  <div>
    <home-header > </home-header>
    <home-swiper :list="swiperList"> </home-swiper>
    <home-icons :list="iconList"> </home-icons>
    <home-recommend :list="recommendList"> </home-recommend>
    <home-weekend :list="weekendList"> </home-weekend>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
import axios from 'axios'
import { mapState } from 'vuex'


export default {
  name: "Home",
  components:{
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommend,
    HomeWeekend
  },
  data(){
    return {
      swiperList:[],
      iconList:[],
      recommendList:[],
      weekendList:[],
      lastCity:''
    }
  },
  computed:{
    ...mapState(['city'])
  },
  methods:{
    getAjax(){
	//返回数据后执行getAjaxSuc函数
      axios.get('/api/index.json?city='+this.city)
        .then(this.getAjaxSuc)
    },
    getAjaxSuc (res){
	//res下有data属性
      res=res.data
	  //判断数据是否返回成功
      if(res.ret&&res.data){
        const data=res.data
        this.swiperList=data.swiperList
        this.iconList=data.iconList
        this.recommendList=data.recommendList
        this.weekendList=data.weekendList
      }
      console.log(res)
    }
  },
  mounted (){
    //保存上一次的城市
    this.lastCity=this.city;
    this.getAjax()
  },
  activated(){
    //判断城市是否改变
    if(this.lastCity!==this.city){
      this.lastCity=this.city;
      //重新发送ajax请求
      this.getAjax();
    }
  }

    }
</script>

<style>

</style>
