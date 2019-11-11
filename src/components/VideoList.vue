<template>

  <ul class="list-group">
    <VideoListItem v-for="video in videos" :key="video.etag" :video="video" @videoSelect="onVideoSelect"/>
  </ul>

</template>

<script>
import VideoListItem from './VideoListItem.vue'

export default {
  name: 'VideoList',

  props: {
    videos: Array,
  },

  components: {
    VideoListItem,
  },

  methods: {
    onVideoSelect(video) {
      this.$emit('videoSelect', video)
    }
  }
}
</script>

<style>

</style>