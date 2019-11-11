<template>

  <div v-if="video">
    <div id="video-detail">

      <iframe :src="videoURL" frameborder="0" class="w-100 h-75"></iframe>

      <h4>{{video.snippet.title}}</h4>
      <p>{{video.snippet.description}}</p>

    </div>
  </div>

</template>

<script>
export default {
  name: 'VideoDetail',

  props: {
    video: Object
  },

  computed: {
    videoURL() {
      const videoID = this.video.id.videoID

      return `https://www.youtube.com/embed/${videoID}`
    }
  }
}
</script>

<style>
#video-detail {
  width: 75rem;
  height: 50rem;
}
</style>