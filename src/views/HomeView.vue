<template>
  <div class="container">
    <MealButton :btnText="btnText" @click="generateMeal" />
    <br />
    <Meal :meal="meal" v-if="meal" />
  </div>
</template>

<script>
import MealButton from "../components/MealButton.vue";
import Meal from "../components/Meal.vue";
import axios from "axios";
export default {
  data() {
    return {
      mealGenerated: false,
      meal: null,
    };
  },
  computed: {
    btnText() {
      return this.mealGenerated ? "Generate Another Meal" : "Generate Meal";
    },
  },
  components: { MealButton, Meal },
  methods: {
    generateMeal() {
      this.mealGenerated = true;
      this.meal = null;

      axios
        .get("https://www.themealdb.com/api/json/v1/1/random.php")
        .then((res) => {
          console.log(res);
          this.meal = res.data.meals[0];
        });
    },
  },
};
</script>

<style lang="scss" scoped>
.container {
  display: flex;
  flex-direction: column;
  padding-top: 1rem;
}
</style>
