<script>
import Product from './Product.vue';

export default {
  components: {
   Product,
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