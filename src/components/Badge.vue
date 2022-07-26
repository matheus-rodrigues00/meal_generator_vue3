<template>
  <div class="badge-container">{{ tagText }}</div>
</template>

<script>
export default {
  props: {
    tagText: {
      required: true,
      type: String,
    },
  },
};
</script>

<style lang="scss" scoped>
.badge-container {
  border-radius: 16px;
  padding: 4px 12px;
  background: #ffdeb4;
  text-align: center;
  color: #3c3d3f;
  font-weight: 700;
}
</style>
