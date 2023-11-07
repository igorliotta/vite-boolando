<script>
import Product from './Product.vue'
import productJson from '../db.json'

export default {
  components: {
   Product,
  },
  data() {
    return {
      product: productJson,
    }
  },
  created() {
    console.log(this.product)
  }
}
</script>

<template>
  <main class="main-content">
    <div class="container">
      <div class="row">
        <Product />
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