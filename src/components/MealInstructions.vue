<template>
  <div>
    <h2>{{ mealTitle }}</h2>
    <p>
      {{ mealInstructions }}
    </p>
  </div>
</template>

<script>
export default {
  props: {
    mealTitle: {
      type: String,
      required: true,
    },
    mealInstructions: {
      type: String,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped></style>
