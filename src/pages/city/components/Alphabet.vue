<template>
  <ul class="list">
    <li class="item"
        v-for="item of letters"
        :key="item"
        :ref="item"
        @click="handleLetterClick"
        @touchstart.prevent="handleTouchStart"
        @touchmove="handleTouchMove"
        @touchend="handleTouchEnd"
        >
    {{item}}</li>
  </ul>
</template>

<script>
  export default {
    name: "CityAlphabet",
    props:{
      cities:Object
    },
    data(){
      return {
        //标识符
        startStatus:false,
        startY:0,
        timer:null
      }
    },
    //页面数据更新时
    updated(){
      this.startY=this.$refs['A'][0].offsetTop
    },
    computed:{
      //['A','B',...]
      letters(){
        const letters=[];
        for(let i in this.cities){
          letters.push(i);
        }
        return letters;
      }
    },
    methods:{
	//点击字母 滚到对应位置
      handleLetterClick(e){
        this.$emit('change',e.target.innerText);
      },
      handleTouchStart(){
        this.startStatus=true
      },
      handleTouchMove(e){
        if(this.startStatus){
          if(this.timer){
            clearTimeout(this.timer)
          }
          this.timer=setTimeout(()=>{
            const startY=this.startY;
            //点击元素的位置=点击元素的位置-A元素的位置
            const touchY=e.touches[0].clientY-79;
            //当前元素的下标
            const index=Math.floor((touchY-startY)/20);
            if(index>=0&&index<this.letters.length){
              //将点击字母发送给父元素
              this.$emit('change',this.letters[index])
            }
          },16)
        }
      },
      handleTouchEnd(){
        this.startStatus=false
      }
    }
  }
</script>

<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
.list
  display: flex
  flex-direction: column
  justify-content: center
  position: absolute
  top: 1.58rem
  right: 0
  bottom: 0
  width: .4rem
.item
  line-height: .4rem
  text-align: center
  color: $bgColor;
</style>
