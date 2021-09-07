<template>
  <section>
    <div class="hottop">
      <div class="hotopct">
        <div class="u-hmsprt hoticon"></div>
        <div class="hottime">更新日期:09月06日</div>
      </div>
    </div>
    <ul>
      <MusicListItem
      ></MusicListItem>
       <SongListItem
         @change-current-song="
          $emit('change-current-song', item);
          $emit('change-current-play-list', tracks);
        "
        :currentSongId="currentSongId"
        :playing="playing"
        v-for="(item, index) in tracks"
        :key="item.id"
        :item="item"
        :index="index"
        :class="{ lt3: index < 3 }"
        >{{ (index + 1).toString().padStart(2, 0) }}
      </SongListItem>
      
    </ul>
  </section>
</template>

<script>
 import MusicListItem from "../components/MusicListItem.vue";
import SongListItem from "@/components/SongListItem.vue";
export default {
  components: {
    MusicListItem,
    SongListItem,
  },
  props:{
    currentSongId:{
      type:Number,
    },
    playing:Boolean,
  },
  data: function () {
    return {
      tracks: [],
    };
  },
  created() {
    this.axios.get("http://apis.netstart.cn/music/playlist/detail/?id=3778678").then((res) => {
      this.tracks = res.data.playlist.tracks;
    });
  },
};
</script>

<style lang="less">
.hottop {
  position: relative;
  padding-top: 38.9%;
  overflow: hidden;
  background: url("../assets/hot_music_bg_2x.jpg") no-repeat;
  background-size: contain;
  .hotopct {
    display: flex;
    -webkit-box-orient: vertical;
    -webkit-box-direction: normal;
    flex-direction: column;
    -webkit-box-pack: center;
    justify-content: center;
    position: absolute;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    z-index: 0;
    padding-left: 20px;
    box-sizing: border-box;
    .hoticon {
      width: 142px;
      height: 67px;
      background: url("../assets/index_icon_2x.png") no-repeat;
      background-position: -24px -30px;
      background-size: 166px 97px;
    }
    .hottime {
      margin-top: 10px;
      color: hsla(0, 0%, 100%, 0.8);
      font-size: 12px;
      transform: scale(0.91);
      transform-origin: left top;
    }
  }
}
</style>
