<template>
  <div class="store" v-if="isVisible">
    <div class="card border-0 shadow">
      <div class="card-body">
      <h2 class="store__title">{{ title }}</h2>
      <span class="store__location">{{ location }}</span>
      <img :src="photo" :alt="title" :title="title" class="img-fluid" />
      </div>
    </div>
  </div>
</template>

<style lang="scss">
@import './Store.scss';
</style>

<script>
export default {
  name: 'Store',
  props: {
    title: {
      type: String,
      default: null
    },
    location: {
      type: String,
      default: null
    },
    photo: {
      type: String,
      default: null
    }
  },
  computed: {
    isVisible () {
      return !!this.title && !!this.location;
    }
  }
}
</script>
