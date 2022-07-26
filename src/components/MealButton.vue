<template>
  <button>{{ btnText }}</button>
</template>

<script>
export default {
  props: {
    btnText: {
      type: String,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>
button {
  border: none;
  outline: none;
  cursor: pointer;
  padding: 8px 24px;
  border-radius: 16px;
  text-align: center;
  font-weight: 700;
  background: #fff9ca;
  color: #b2a4ff;
  text-transform: uppercase;
  margin: 0 auto;
}
</style>
