<template>
  <div v-if="video">
    <h3>비디오</h3>
    <iframe width="300" height="300" :src="videoUrl" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  </div>
</template>

<script>
export default {
    name : 'VideoDetail',
    props : {
        video : {
            type: Object,
        }
    },
    computed:{
        videoUrl() {
            return `https://youtube.com/embed/${this.video.id.videoId}/`
        }
    }
}
</script>

<style>
    iframe {
        width:500px;
    }
</style>