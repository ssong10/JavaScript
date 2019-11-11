<template>
  <div>
    <h2>영상목록</h2>
    <ul class="list-group">
      <VideoListItem v-for="video in videos" :key="video.id.videoId" :video="video" @video-select-event="selectvideo(video)"/>
    </ul>
  </div>
</template>

<script>
import VideoListItem from './VideoListItem.vue'
export default {
  name:"VideoList",
  components :{
    VideoListItem
  },
  props: {
      videos : {
          type: Array,
          required : true
      }
  },
  methods:{
    selectvideo(value) {
      this.$emit('video-select-event',value)
    }
  }
}
</script>

<style scoped>
/* scoped : 해당 컴포넌트에서만 사용되는 style */
img{
  width:360px;
}
li {
  cursor :pointer;
}
li:hover {
  background-color: #fffff2;
}
</style>