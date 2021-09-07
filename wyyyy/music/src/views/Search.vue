<template>
<section>
  <div class="m-input">
  <div class="search ">
      <span class="searchicon"></span>
    <input type="text" placeholder="搜索歌曲、歌手、专辑" v-model="value"/>
  </div>
  </div>
 
<Suggest :value="value" :lists="lists"/>
 <HotSearch :hotlists="hotlists" v-if="!value" />
</section>
</template>

<script>
import Suggest from "@/components/Suggest.vue";
import HotSearch from "@/components/HotSearch.vue";
export default {
    data:function(){
        return{
          lists:[],
          hotlists:[],
          value:""
        }
    },
    components: {
    Suggest,
    HotSearch,
  },
   watch:{
        value:function(newValue){
        newValue?
      this.axios.get("http://music.kele8.cn/search?keywords=" + newValue)
  .then( (response)=> {
      console.log(response)
    this.lists = response.data.result.songs;
  })
  .catch(function (error) {
    console.log(error);
  })
  :(this.lists=[])
    },
        },
    created(){
    this.axios.get("http://music.kele8.cn/search/hot")
  .then( (response)=> {
      console.log(response)
    this.hotlists = response.data.result.hots;
  })
  .catch(function (error) {
    console.log(error);
  })
    }
}
</script>
<style lang="less">
.m-input{ 
  padding: 15px 10px;
  position: relative;
  &::after{
    position: absolute;
    z-index: 2;
    content: "";
    top: 0px;
    left: 0;
    pointer-events: none;
    box-sizing: border-box;
    transform-origin: top left;
    border: 0 solid rgba(0,0,0,.1);
    border-bottom-width: 1px;
    width: 200%;
    height: 200%;
    transform: scale(.5);
  }
.search {
  position: relative;
  width: 100%;
  height: 30px;
  padding: 0 30px;
  box-sizing: border-box;
  background: #ebecec;
  border-radius: 30px;
  margin: 10px auto;

  input {
    width: 100%;
    height: 30px;
    line-height: 18px;
    background: rgba(0, 0, 0, 0);
    font-size: 14px;
    color: #333;
    border: 0;
    outline: 0;
    line-height: 30px;
  }
  .searchicon{
      position: absolute;
    left: 0;
    top: 8px;
    margin: 0 10px;
    vertical-align: middle;
    width: 13px;
    height: 13px;
    background-image: url(../assets/查找.png);
    background-size: contain;
    color:#ccc
  }
}
}
</style>