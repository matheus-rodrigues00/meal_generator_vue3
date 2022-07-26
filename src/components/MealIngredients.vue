<template>
  <div class="ingredients-container">
    <h3>Ingredients:</h3>
    <ul>
      <li v-for="(ingredient, idx) in ingredients" :key="ingredient + idx">
        {{ ingredient }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    ingredients: {
      required: true,
      type: Array,
    },
  },
};
</script>

<style lang="scss" scoped></style>
