<template>
  <div>
    <h3>Video Recipe:</h3>
    <iframe
      :src="embededVideo"
      frameborder="0"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen
      class="video-recipe"
    ></iframe>
    <br />
    <br />
  </div>
</template>

<script>
export default {
  computed: {
    embededVideo() {
      if (this.video.length > 0) {
        return this.video.replace("watch?v=", "embed/");
      }
      return "";
    },
  },
  props: {
    video: {
      required: true,
      type: String,
    },
  },
};
</script>

<style lang="scss" scoped>
.video-recipe {
  max-width: 100%;
  height: 200px;
}
</style>
