<template>
  <div id="app">
    <div class="container">
      <SearchBar @input-change-event="onInputChange" />
      <VideoDetail :video="selectedVideo"/>
      <VideoList @video-select-event="selectvideo" :videos="videos"/>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import SearchBar from './components/SearchBar.vue'
import VideoList from './components/VideoList.vue'
import VideoDetail from './components/VideoDetail.vue'

const API_KEY = process.env.VUE_APP_API_KEY
export default {
  name: 'app',
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data() {
    return {
      videos: [],
      selectedVideo: null
    }
  },
  methods : {
    onInputChange(value) {
      console.log('==App==')
      console.log(value)
      axios.get('https://www.googleapis.com/youtube/v3/search',{
        params : {
          key : API_KEY,
          part : 'snippet',
          q:value,
          type: "video"
        }
      }).then(response => {
        console.log(response)
        // data의 videos에 저장
        this.videos = response.data.items
      }).catch(error => {
        console.log(error)
      })
    },
    selectvideo(video) {
      this.selectedVideo = video
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
