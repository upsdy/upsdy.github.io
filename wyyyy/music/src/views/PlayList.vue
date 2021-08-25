<template>
  <div v-if="detail">
    <h3>PlayList {{ $route.query.id }}</h3>

    <ul>
      <li v-for="item in detail.tracks" :key="item.id">{{ item.name }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      detail: null,
    };
  },
  methods: {
    getPlayListDetail: function(id) {
      this.axios
        .get("http://apis.netstart.cn/music/playlist/detail", {
          params: {
            id,
          },
        })
        .then((res) => {
          console.log(res);
          this.detail = res.data.playlist;
        });
    },
  },

  created: function() {
    this.getPlayListDetail(this.$route.query.id);
  },
};
</script>

<style lang="less" scoped></style>
