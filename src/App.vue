<template>
  <div class="container">
    <SearchBar @termChange="onTermChange" />

    <div class="row">
      <VideoDetail :video="selectedVideo"/>
      <VideoList :videos="videos" @videoSelect="onVideoSelect" />
    </div>
  </div>
</template>

<script>
import axios from 'axios'

import SearchBar from '@/components/SearchBar'
import VideoDetail from '@/components/VideoDetail'
import VideoList from '@/components/VideoList'

const API_KEY = 'AIzaSyCMKPFG-QkVA7dlcfDfMprORiPvyMmTFsM'

export default {
  components: { SearchBar, VideoDetail, VideoList },

  data() {
    return {
      selectedVideo: null,
      videos: []
    }
  },

  methods: {
    onTermChange(searchTerm) {
      axios
        .get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            key: API_KEY,
            type: 'video',
            part: 'snippet',
            q: searchTerm
          }
        })
        .then(({ data }) => {
          this.videos = data.items
        })
    },

    onVideoSelect(video) {
      this.selectedVideo = video
    }
  }
}
</script>

<style></style>
