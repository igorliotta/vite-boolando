<script>
import Card from './Card.vue'
// import productsJson from '../db.json'
import { store } from '../store'

export default {
  components: {
    Card,
  },
  data() {
    return {
      // products: productsJson.products,
      store: store
    }
  },
  created() {
    // console.log(this.products)
    console.log(this.store)
  }
}
</script>

<template>
  <main class="main-content">
    <div class="container">
      <div class="row">
      <Card v-for="product in store.products"
      :item="product" />
    </div>
    </div>
  </main>
</template>

<style lang="scss" scoped>

.main-content {
  padding: 20px 20px;
}

.row {
  row-gap: 10px;
}

</style>