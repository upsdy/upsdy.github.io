<template>
  <section class="m-hotlist">
    <h3>热门搜索</h3>
    <ul class="list">
      <li v-for="item in hotlists"
        :key="item.id"
        class="item f-bd f-bd-full" 
        @click="
        value = item.first;
      ">
        {{ item.first }}
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  props: {
    hotlists: Array,
    detail:Array,
  },
};
</script>

<style lang="less" scoped>
.m-hotlist {
  padding: 15px 10px 0;
  .h3 {
    font-size: 12px;
    line-height: 12px;
    color: #666;
  }
  .list {
    margin: 10px 0 7px;
    .item {
      display: inline-block;
      height: 32px;
      margin-right: 8px;
      margin-bottom: 8px;
      padding: 0 14px;
      font-size: 14px;
      line-height: 32px;
      color: #333;
      &::after {
        border-color: #d3d4da;
        border-radius: 32px;
      }
    }
    .f-bd {
      position: relative;
      &::after {
        width: 200%;
        height: 200%;
        transform: scale(0.5);
        position: absolute;
        z-index: 2;
        content: "";
        top: 0;
        left: 0;
        pointer-events: none;
        box-sizing: border-box;
        transform-origin: top left;
        border: 0 solid rgba(0, 0, 0, 0.1);
        border-width: 1px;
      }
    }
  }
}
</style>