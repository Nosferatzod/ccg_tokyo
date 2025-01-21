<template>
  <div class="main-content">
    <h1>CCG</h1>
    <img src="../assets/images/Arima.gif" alt="">
  </div>
</template>

<script>
export default {
  name: 'MainContent' // Mudança aqui: Nome do componente agora é "MainContent"
}
</script>

<style scoped>
.main-content {
  background-color: #222;
  padding: 20px;
  text-align: center;
  color: #fff;
  font-family: 'Arial', sans-serif;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.5);
}
.main-content h1 {
  font-size: 3rem;
  letter-spacing: 2px;
  text-transform: uppercase;
}
</style>
