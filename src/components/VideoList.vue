<template>
  <ul class="list-group col-md-4">
    <VideoListItem v-for="(video, idx) in videos" :key="idx" :video="video" @videoSelect="onVideoSelect" />
  </ul>
</template>

<script>
import VideoListItem from './VideoListItem'

export default {
  name: 'VideoList',

  components: {
    VideoListItem
  },

  props: {
    videos: Array
  },

  methods: {
    onVideoSelect(video) {
      this.$emit('videoSelect', video)
    }
  }
}
</script>

<style></style>
