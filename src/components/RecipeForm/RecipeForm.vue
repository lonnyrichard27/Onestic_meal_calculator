<template>
  <div class="container-fluid">
    <p>Introduce below the quantity for each ingredient you have and we will calculate how many Pasta Carbonara meals you can cook!</p>
      <label class="mt-3">Eggs:</label>
      <input class="form-control" type="number" v-model="myeggs" name="eggs" id="recipe-eggs" value="0" />
      <label for="recipe-pasta" class="mt-3">Pasta</label>
      <input class="form-control" type="number" v-model="mypasta" name="pasta" id="recipe-pasta" value="0" />
      <label for="recipe-butter" class="mt-3">Butter</label>
      <input class="form-control" type="number" v-model="mybutter" name="butter" id="recipe-butter" value="0" />
      <label for="recipe-milk" class="mt-3">Milk</label>
      <input class="form-control" type="number" v-model="mymilk" name="milk" id="recipe-milk" value="0" />
      <label for="recipe-oil" class="mt-3">Oil</label>
      <input class="form-control" type="number" v-model="myoil" name="oil" id="recipe-oil" value="0" />
      <label for="recipe-bacon" class="mt-3">Bacon</label>
      <input class="form-control" type="number" v-model="mybacon" name="bacon" id="recipe-bacon" value="0" />
      <button class="btn btn-success my-3" @click="calculate">Calculate</button>
  </div>
</template>
<style lang="scss">
@import './RecipeForm.scss';
</style>
<script>
export default {
  name: 'RecipeForm',
  data () {
    return {
      meals: 0,
      mymilk: null,
      mypasta: null,
      mybacon:null,
      myoil: null,
      myeggs: null,
      mybutter: null,
      userRecipe: []
    };
  },
  props: {
    ingredients: {
      type: Object,
      default: () => ({})
    }
  },
  methods: {
    calculate (event) {
      event.preventDefault();
      const milk = Math.floor(this.mymilk / this.ingredients.milk)
      const pasta = Math.floor(this.mypasta / this.ingredients.pasta)
      const bacon = Math.floor(this.mybacon / this.ingredients.bacon)
      const oil = Math.floor(this.myoil / this.ingredients.oil)
      const eggs = Math.floor(this.myeggs / this.ingredients.eggs)
      const butter = Math.floor(this.mybutter / this.ingredients.butter)
      this.meals = Math.min(milk, pasta, bacon, oil, eggs, butter)
      
      const yourRecipe = {
        milk : milk,
        pasta: pasta,
        bacon: bacon,
        oil: oil,
        eggs: eggs,
        butter: butter,
      }
       console.log(yourRecipe);
       this.userRecipe.push(yourRecipe)
      sessionStorage.setItem('user_recipe', JSON.stringify(this.userRecipe))
      this.$router.push({ name: 'Result', params:{number: this.meals}})
    }
  }
}
</script>
