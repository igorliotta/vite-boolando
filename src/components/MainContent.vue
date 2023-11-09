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
      open: false,
      currentProduct: {}
    }
  },
  methods: {
    showModal(product) {
      console.log('show modal',product)
      this.open = true
      this.currentProduct = product;
    },
    closeModal() {
      console.log('close modal')
      this.open = false
      this.currentProduct = {}
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
      <Card @show="showModal" v-for="product in store.products"
      :item="product" />
    </div>
    </div>

    <div v-if="open" class="modal">
      <div class="modal-card">
        <div class="modal-card-header">
          <figure class="miniature">
            <img class="miniature-img miniature-front-img" :src="'/img/' + currentProduct.frontImage" alt="">
            <img class="miniature-img miniature-back-img" :src="'/img/' + currentProduct.backImage" alt="">
          </figure>
        </div>
        <div class="modal-card-body">
          <font-awesome-icon class="mark" @click="closeModal()" icon="fa-solid fa-circle-xmark" />
         <div class="info-product">
          <p>
            <span class="decoration-text">Brand:</span> <span class="weight-text">{{ currentProduct.brand }}</span>
          </p>
          <p>
           <span class="decoration-text">Type of Product:</span> <span class="weight-text">{{ currentProduct.name }}</span>
          </p>
          <p>
           <span class="decoration-text">Price:</span> <span class="weight-text">{{ currentProduct.price }}</span>
          </p>
         </div>
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

.modal .modal-card{
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
  z-index: 50;
  background-color: white;
  border-radius: 15px;
  padding: 20px;
  width: 100%;
  max-width: 550px;
  box-shadow: 0px 0px 20px rgb(255, 115, 0);
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.modal::after {
  content: '';
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 40;
  background-color: rgba(0, 0, 0, 0.7);
}

.modal-card-header {
  display: flex;
  justify-content: space-between;
  font-weight: 700;
}

.miniature {
  width: 230px;
  aspect-ratio: 9/12;
  border: 3px solid rgba(0, 0, 0, 0.5);
  position: relative;
}

.miniature-img {
  width: 100%;
  aspect-ratio: 9/12;
  padding: 10px;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
}

.miniature-front-img {
  opacity: 1;
}

.miniature-front-img:hover {
  opacity: 0;
}

.miniature-back-img {
  opacity: 0;
}

.miniature-back-img:hover {
  opacity: 1;
}

.modal-card-body {
  height: 300px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  position: relative;
  gap: 5px;
}

.info-product {
  text-align: left;
  font-size: 13px;
}

.mark {
  position: absolute;
  top: 0;
  right: 0;
}

.decoration-text {
  padding: 5px;
  text-decoration: underline;
}

.weight-text {
  font-weight: 700;
}


</style>