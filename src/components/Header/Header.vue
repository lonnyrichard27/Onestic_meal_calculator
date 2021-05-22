<template>
  <div class="bg-dark">
    <ul class="nav justify-content-center">
      <li class="nav-item">
        <router-link to="/" class="nav-link active text-white">Home</router-link>
      </li>
      <li class="nav-item">
        <router-link to="/meals" class="nav-link text-white">Carbonara Meals Calculator</router-link>
      </li>
      <li class="nav-item">
        <router-link to="/restaurants" class="nav-link text-white">Our Restaurants</router-link>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name: 'Header'
}
</script>
