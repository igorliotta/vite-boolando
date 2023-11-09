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
    }
  },
  methods: {
    showModal() {
      console.log('show modal')
      this.open = true
    },
    closeModal() {
      console.log('close modal')
      this.open = false
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
          <span>
            Titolo
          </span>
          <font-awesome-icon @click="closeModal()" icon="fa-solid fa-circle-xmark" />
        </div>
        <div class="modal-card-body">
          <p>Contenuto del modale</p>
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
  box-shadow: 0px 0px 20px rgba(238, 109, 3, 1);
}

.modal::after {
  content: '';
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 40;
  background-color: rgba(0, 0, 0, 0.6);
}

.modal-card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}



</style>