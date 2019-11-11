<template>

  <li class="list-group-item" @click="onVideoSelect">

    <img :src="thumbnailURL" class="m-1">

    {{video.snippet.title}}

  </li>

</template>

<script>
export default {
  name: 'VideoListItem',

  props: {
    video: Object
  },

  computed: {
    thumbnailURL() {
      return this.video.snippet.thumbnails.default.url
    }
  },

  methods: {
    onVideoSelect() {
      this.$emit('videoSelect', this.video)
    }
  }
}
</script>

<style>

</style>