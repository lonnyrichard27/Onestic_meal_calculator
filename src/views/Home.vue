<template>
  <div class="page page__home">
    <h3 class="my-5">{{ welcomeMessage }}</h3>
  </div>
</template>

<script>
import moment from 'moment';

export default {
  name: 'Home',
  data () {
    return {
      currentTime: moment().format('dddd, MMMM Do YYYY, h:mm:ss a')
    }
  },
  computed: {
    welcomeMessage () {
      return 'Welcome! Your local time is: ' + this.currentTime;
    }
  },
  mounted() {
    const setTimer = () => setTimeout(() => {
      this.currentTime = moment().format('dddd, MMMM Do YYYY, h:mm:ss a');
      setTimer();
    }, 1000);
    setTimer();
  }
}
</script>
