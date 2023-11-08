<script>

export default {
  data() {
    return {
      types: ['Uomo','Donna','Bambino'],
      headerLogo: '/img/boolean-logo.png',
    }
  },
  methods: {

  }
}

</script>

<template>
  <header class="page-header">
    <nav class="row navbar">
      <ul class="list">
        <li>
          <a href="#">{{ types[0] }}</a>
        </li>
        <li>
          <a href="#">{{ types[1] }}</a>
        </li>
        <li>
          <a href="#">{{ types[2] }}</a>
        </li>
      </ul>
      <img class="img-logo" :src="headerLogo" alt="">
      <ul class="list">
        <li>
          <a href="#"><font-awesome-icon icon="fa-solid fa-user" /></a>
        </li>
        <li>
          <a href="#"><font-awesome-icon icon="fa-solid fa-heart" /></a>
        </li>
        <li>
          <a href="#"><font-awesome-icon icon="fa-solid fa-cart-shopping" /></a>
        </li>
      </ul>
    </nav>
  </header>
</template>

<style lang="scss" scoped>
@use '../styles/partials/varibles' as *;
.page-header {
  width: 1200px;
  background-color: $header-color;
  padding: 20px;
  margin: 0 auto;
}

.navbar {
  justify-content: space-between;
}

.img-logo {
  width: 200px;
  height: 45px;
}

.list {
  display: flex;
  gap: 10px;
  align-items: center;
  color: white;
}




</style>
