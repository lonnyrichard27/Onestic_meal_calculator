<template>
  <div class="store-list">
    <p>Here you can find all of our restaurants. </p>
     <p> We have <b>{{ storesCount }}</b> stores right now!</p>
    <div class="container">
      <div class="row">
        <div class="col-lg-3 col-md-4 col-6 my-2" v-for="store in storesWithImages" :key="store.id">
          <Store class="store-list__item" :title="store.name" :photo="store.image" :location="store.location"  />
        </div>
      </div>
    </div>
  </div>
</template>
<style lang="scss">
@import './StoreList.scss';
</style>
<script>
import Store from '@/components/Store/Store';
import _ from 'lodash';

export default {
  name: 'StoreList',
  components: {
    Store
  },
  props: {
    stores: {
      type: Array,
      default: () => []
    }
  },
  computed: {
    storesWithImages () {
      return _.map(this.stores, function (store) {
        store['image'] = 'https://via.placeholder.com/300?text=' + store.name;

        return store;
      });
    },
    storesCount () {
      return _.size(this.stores);
    }
  }
}
</script>
