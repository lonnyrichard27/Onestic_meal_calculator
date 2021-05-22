<template>
  <div class="page page__carbonara">
    <h1 class="mt-4">Pasta carbonara meals</h1>
    <div class="page__carbonara-meals">
      <RecipeForm :ingredients="secretIngredients"/>
    </div>
  </div>
</template>
<script>
import RecipeForm from '@/components/RecipeForm/RecipeForm';
const secretIngredients = require('@/assets/secret.json')

export default {
  name: 'Meals',
  components: {
    RecipeForm
  },
  data () {
    return {
      secretIngredients
    }
  }
}
</script>
