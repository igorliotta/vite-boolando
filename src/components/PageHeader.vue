<script>

</script>

<template>
  <header class="page-header">
    <nav class="row navbar">
      <ul class="list">
        <li>
          <a href="#">Uomo</a>
        </li>
        <li>
          <a href="#">Donna</a>
        </li>
        <li>
          <a href="#">Bambino</a>
        </li>
      </ul>
      <img class="img-logo" src="/img/boolean-logo.png" alt="">
      <ul class="list">
        <li>Icona</li>
        <li>Icona</li>
        <li>Icona</li>
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
