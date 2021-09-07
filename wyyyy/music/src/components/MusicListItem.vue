<template>
  <li class="musiclist-item" @click="$emit('change-current-play-song', item)">
    <div class="index" v-if="index !== undefined">
      {{ (index + 1).toString().padStart(2, 0) }}
    </div>
    <div class="detail">
      <h3 style="margin-bottom: 5px">{{ item.name }}</h3>
      <p style="color:#999">
        <span
          class="artist"
          v-for="artist in item.song ? item.song.artists : item.ar"
          :key="artist.id"
        >
          {{ artist.name }}
        </span>
        <i class="album">{{
          item.song ? item.song.album.name : item.al.name
        }}</i>
      </p>
    </div>
    <div class="icon"></div>
  </li>
</template>

<script>
export default {
  props: {
    item: Object,
    index: Number,
  },
};
</script>

<style lang="less">
.musiclist-item {
  display: flex;
  padding: 10px 0;
  align-items: center;
  border-bottom: 1px solid lightgray;
  padding-right: 10px;
  margin-left: 10px;
  
  .index {
    margin: 0 10px;
    color: #999;
  }
  &:nth-child(1),
  &:nth-child(2),
  &:nth-child(3) {
    .index {
      color: red;
    }
  }
  .detail {
    flex: 1;

    p {
      display: -webkit-box;
      -webkit-line-clamp: 1;
      -webkit-box-orient: vertical;
      overflow: hidden;
      font-size: 12px;
      .artist {
        &::after {
          content: "/";
        }
      }
      i {
        font-style: normal;
      }
    }
    span {
      &:last-of-type {
        &::after {
          content: " - ";
        }
      }
    }
  }
  .icon {
    width: 22px;
    height: 22px;
    background: url("../assets/index_icon_2x.png");
    background-size: 166px 97px;
    background-position: -24px 0;
  }
}
</style>