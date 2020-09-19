<template>
  <div v-if="video" class="col-md-8">
    <div class="embed-responsive embed-responsive-16by9">
      <iframe
        width="560"
        height="315"
        :src="videoUrl"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen
      ></iframe>
    </div>
    <div class="details">
      <h1>{{ title }}</h1>
      <p>{{ description }}</p>
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
    title() {
      return this.video ? this.video.snippet.title : null
    },

    description() {
      return this.video ? this.video.snippet.description : null
    },

    videoUrl() {
      if (this.video) {
        const embedUrl = 'https://www.youtube.com/embed/'
        const { videoId } = this.video.id
        return `${embedUrl}${videoId}`
      } else {
        return null
      }
    }
  }
}
</script>

<style scoped>
.details {
  margin-top: 10px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
}
</style>
