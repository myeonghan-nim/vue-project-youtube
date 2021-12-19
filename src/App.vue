<template>
  <div class="container">
    <div class="py-3">
      <button class="btn btn-danger position-absolute top-0">YouTube</button>
      <SearchBar class="my-1" @inputChange="onInputChange"/>
    </div>
    <VideoDetail :video="selectedVideo"/>
    <VideoList :videos="videos" @videoSelect="onVideoSelect"/>
  </div>
</template>

<script>
import axios from 'axios'

import SearchBar from './components/SearchBar.vue'
import VideoList from './components/VideoList.vue'
import VideoDetail from './components/VideoDetail.vue'

const API_KEY = process.env.VUE_APP_YOUTUBE_API_KEY
const API_URL = 'https://www.googleapis.com/youtube/v3/search'

export default {
  name: 'App',
  data() {
    return {
      videos: [],
      selectedVideo: null,
    }
  },
  components: {
    SearchBar,
    VideoList,
    VideoDetail,
  },
  methods: {
    onInputChange(inputValue) {
      axios.get(API_URL, {
        params: {
          key: API_KEY,
          part: 'snippet',
          type: 'video',
          q: inputValue
        }
      })
        .then((res) => {
          this.videos = res.data.items
        })
        .catch((err) => {
          console.log(err)
        })
    },
    onVideoSelect(video) {
      this.selectedVideo = video
    }
  }
}
</script>

<style>
</style>
