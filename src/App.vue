<template>
  <div class="container">

    YouTube

    <!-- 3. use components -->
    <!-- child-component @function-from-child="function-in-parent" -->
    <SearchBar @inputChange="onInputChange"/>

    <!-- child-component :datas-to-child="datas-in-parent" -->
    <VideoDetail :video="selectedVideo"/>
    <VideoList :videos="videos" @videoSelect="onVideoSelect"/>

  </div>
</template>

<script>
// 1. load components
import SearchBar from './components/SearchBar.vue'
import VideoList from './components/VideoList.vue'
import VideoDetail from './components/VideoDetail.vue'

import axios from 'axios'

const API_KEY = process.env.VUE_APP_YOUTUBE_API_KEY
const API_URL = 'https://www.googleapis.com/youtube/v3/search'

export default {
  name: 'App',  // define component name

  data() {
    return {
      videos: [],
      selectedVideo: null,
    }
  },

  // 2. add components
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
        .then((response) => {
          this.videos = response.data.items
        })
        .catch((error) => {
          console.log(error)
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