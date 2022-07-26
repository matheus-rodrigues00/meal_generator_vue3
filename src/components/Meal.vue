<template>
  <div class="row">
    <div class="col-12 col-md-4">
      <img :src="mealImg" v-if="mealImg" class="meal-image" />
      <br />
      <br />
      <MealIngredients
        :ingredients="mealIngredients"
        v-if="mealIngredients.length > 0"
      />
      <br />
      <MealVideoRecipe :video="videoRecipe" v-if="videoRecipe" />
    </div>
    <div class="col-12 col-md-8">
      <div class="badge-container mb-3" v-if="mealTags">
        <Badge v-for="(tag, idx) in mealTags" :key="tag + idx" :tagText="tag" />
      </div>

      <MealInstructions
        :mealTitle="mealTitle"
        :mealInstructions="mealInstructions"
      />
    </div>
  </div>
</template>

<script>
import MealInstructions from "./MealInstructions.vue";
import MealIngredients from "./MealIngredients.vue";
import MealVideoRecipe from "./MealVideoRecipe.vue";
import Badge from "./Badge.vue";
export default {
  props: {
    meal: {
      required: true,
      type: Object,
    },
  },
  components: { MealInstructions, MealIngredients, MealVideoRecipe, Badge },
  data() {
    return {
      mealImg: null,
      mealTitle: null,
      mealInstructions: null,
      videoRecipe: null,
      mealIngredients: [],
      mealTags: null,
    };
  },
  methods: {
    assignValuesToMealVariables() {
      this.mealImg = this.meal.strMealThumb;
      this.mealTitle = this.meal.strMeal;
      this.mealInstructions = this.meal.strInstructions;
      this.videoRecipe = this.meal.strYoutube;
      if (this.meal.strTags) {
        this.mealTags = this.meal.strTags.split(",");
      }
      this.assignIngredients();
    },
    assignIngredients() {
      for (let i = 1; i <= 20; i++) {
        if (
          this.meal["strIngredient" + i] !== "" &&
          this.meal["strIngredient" + i]
        ) {
          this.mealIngredients.push(
            `${this.meal["strIngredient" + i]} - ${this.meal["strMeasure" + i]}`
          );
        } else {
          break;
        }
      }
    },
  },
  mounted() {
    this.assignValuesToMealVariables();
  },
};
</script>

<style lang="scss" scoped>
.meal-image {
  max-width: 100%;
}
.badge-container {
  display: flex;
  gap: 1rem;
}
</style>
