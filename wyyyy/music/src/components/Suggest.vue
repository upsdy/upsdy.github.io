<template>
 <section class="m-recom">
   <h5 class="title f-bd" v-if="value">搜索 "{{value}}"</h5>
  <ul>
    <li class="recomitem" v-for="item in lists.slice(0,6)" :key="item.id">
      <i class="icon"></i>
      <span class="f-bd">{{item.name}}</span>
    </li>
  </ul>
 </section>
</template>

<script>
export default {
  props:{
   lists:Array,
   newValue:String,
   value:String
  },
}
</script>

<style lang=less>
.title{
  /* height: 50px;
    margin-left: 10px;
    padding-right: 10px;
    font-size: 15px;
    line-height: 50px;
    color: #507daf; */
}
 li.recomitem{
    display: flex;
      align-items: center;
    height: 45px;
    padding-left: 10px;
  .icon{
    width: 15px;
    height: 15px;
    background-image: url(../assets/查找.png);
    display: inline-block;
    vertical-align: middle;
    background-position: 0 0;
    background-size: contain;
    background-repeat: no-repeat;
    margin: 0px 7px;
    }
    .f-bd{
      position: relative;
    display: inline-block;
    -webkit-box-flex: 1;
    flex: 1;
    width: 1%;
    padding-right: 10px;
    font-size: 15px;
    line-height: 45px;
    color: #333;
     /* border-bottom: 1px solid #ccc; */
     overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    word-break: normal;
    &::after{
      position: absolute;
    z-index: 2;
    content: "";
    top: 0;
    left: 0;
    pointer-events: none;
    box-sizing: border-box;
    transform-origin: top left;
    border: 0 solid rgba(0,0,0,.1);
    border-bottom-width: 1px;
    width: 200%;
    height: 200%;
    transform: scale(.5)
    }
    }
    
  }
</style>