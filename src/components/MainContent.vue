<script>
import Card from './Card.vue'
// import productsJson from '../db.json'
import { store } from '../store'
import axios from 'axios'

export default {
  components: {
    Card,
  },
  data() {
    return {
      // products: productsJson.products,
      store: store,
      productsUrl: 'http://localhost:3000/products',
    }
  },
  created() {
    // console.log(this.products)
    axios.get(this.productsUrl).then(res => {
      console.log(res.data)
      this.store.products = res.data;
    });

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