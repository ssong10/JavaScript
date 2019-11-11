<template>
  <li @click="selectedVideo" class ="list-group-item mb-3">
    <img :src="video.snippet.thumbnails.high.url" :alt="video.snippet.title">
    <h3>{{ video.snippet.title }}</h3>
    <p>{{video.snippet.description}}</p>
  </li>
</template>

<script>
export default {
  name : "VideoListItem",
  props: {
    video : {
      type: Object,
      required : true
    }
  },
  methods:{
    selectedVideo() {
      this.$emit('video-select-event',this.video)
      // window.open(`https://www.youtube.com/watch?v=${this.video.id.videoId}/`)
    }
  }
}
</script>

<style scoped>
img {
  width : 360px;
}
</style>