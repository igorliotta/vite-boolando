<script>
import Product from './Product.vue'
import productsJson from '../db.json'

export default {
  components: {
   Product,
  },
  data() {
    return {
      products: productsJson.products
    }
  },
  created() {
    console.log(this.products)
  }
}
</script>

<template>
  <main class="main-content">
    <div class="container">
      <div class="row">
        <div v-for="n in 6" 
        :key="n" 
        class="col-4">
          <Product />
        </div>
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