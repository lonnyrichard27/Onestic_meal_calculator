<template>
  <div class="store-list">
    <h1>With your recipe you can cook {{ number }}Meals</h1>
    <h3 class="mt-4">Below is our secret ingredients formula </h3>
    <div class="my-3" v-for="(value, key) in secretIngredients" :key="key">
        {{ key }} : {{value}}
    </div>
    <h3 class="mt-4">Below is the quantity of each ingredient you have to use</h3>
    <div v-for="(value, key, id) in myIngredients[0]" :key="id" class="my-3">
        {{ key }} : {{value}}
    </div>
    <div class="container">
            <h3 class="my-3">Heres a list of our stores</h3>
        <div class="row">
            <div class="col-lg-4 col-md-6 col-sm-12" v-for="(store,index) in stores" :key="index">
                <Banner :text="store.name" class="banner__text" />
            </div>
        </div>
    </div>
  </div>
</template>

<style lang="scss">
@import '@/components/Banner/Banner.scss';
</style>

<script>
import Banner from '@/components/Banner/Banner.vue'
const stores = require('@/assets/stores/stores.json');
const secretIngredients = require('@/assets/secret.json')

export default {
  components: { Banner },
    props: ['number'],
    data(){
        return{
            stores,
          secretIngredients,
            myIngredients:{}
        }
    },  
    async mounted(){
        this.myIngredients = JSON.parse(sessionStorage.getItem('user_recipe'));
        console.log(this.myIngredients);
    }
}
</script>