<template>
<body>
  <div id="app" :class="{'theme-dark': nightMode}">
    <div class="container-fluid">
      <nav>
        <i class="fas fa-sun icon-sun" aria-hidden="true" v-if="nightMode" @click="nightMode = !nightMode"></i>
        <i class="fas fa-moon icon-moon" aria-hidden="true" v-else @click="nightMode = !nightMode"></i>
      </nav>
    </div>
    <Header />
    <div class="container">
      <router-view/>
    </div>
  </div>
</body>
</template>
<style lang="scss">
 @import url('https://use.fontawesome.com/releases/v5.8.1/css/all.css');
 #app{
 nav {
   position: relative;
   height: 50px;
   i{
    position: absolute;
    top: 10px;
    right: 10px;
    font-size: 1.6rem;
    cursor: pointer;
   }
   .icon-sun {
      color: #FCDA5F;
    }
    .icon-moon {
      color: #041B37;
    }
 }
 &.theme-dark{
   color: white;
   background-color: black;
    .page.page__home{
      color: white;
      background-color: black;
      height: 100vh;
    }
   h2{
     color: black;
   }
   span{
     color: black;
   }
 }
}
</style>
<script>
import Header from '@/components/Header/Header';

export default {
  name: 'App',
  components: {
    Header
  },
  data: () => {
    return{
      nightMode: false
    }
  }
}
</script>