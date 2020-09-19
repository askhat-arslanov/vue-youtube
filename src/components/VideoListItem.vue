<template>
  <li class="list-group-item" @click="onVideoSelect">
    <img :src="thumbnailUrl" alt="Thumbnail" />

    {{ title }}
  </li>
</template>

<script>
export default {
  name: 'VideoListItem',

  props: {
    video: Object
  },

  computed: {
    title() {
      return this.video.snippet.title
    },
    thumbnailUrl() {
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

<style scoped lang="scss">
li {
  cursor: pointer;
  transition: all 0.2s ease;

  &:hover {
    background-color: #eee;
  }
}
</style>
