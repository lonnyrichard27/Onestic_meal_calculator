<template>
  <div class="page page__stores">
    <h5 class="my-4">{{ welcomeMessage }}</h5>
    <h3 class="my-2">Joke Of the Day 😆: {{joke}}</h3>
    <label for="">Search Store:</label>
    <input type="text" v-model="search" @keyup="restaurantFilter">

    <div class="pages__stores-list">
      <StoreList :stores="stores" />
    </div>
  </div>
</template>

<script>
import moment from "moment";
import StoreList from '@/components/StoreList/StoreList';
import axios from "axios"
const stores = require('@/assets/stores/stores.json');

export default {
  name: 'Stores',
  components: {
    StoreList
  },
  data () {
    return {
      currentTime: moment().format('dddd, MMMM Do YYYY, h:mm:ss a'),
      stores,
      search: '',
      joke:null
    }
  },
  computed: {
    welcomeMessage () {
      return 'Welcome to our restaurants list! Your local time is: ' + this.currentTime;
    }
  },
  mounted() {
    const setTimer = () => setTimeout(() => {
      this.currentTime = moment().format('dddd, MMMM Do YYYY, h:mm:ss a');
      setTimer();
    }, 1000);
    setTimer();
    this.getJokes()
  },
  methods: {
   async getJokes(){
     const {data} = await axios.get("https://api.jokes.one/jod?category")
     console.log(data);
     this.joke = data.contents.jokes[0].joke.title
    },
    restaurantFilter(){
      if (!this.search && this.search.length < 2) {
        this.stores = stores
        return
      }

      const search = this.search.toLowerCase()
      this.stores = stores.filter((store) => {
        return store.name.toLowerCase().includes(search)
      })
    }
  }
}
</script>
