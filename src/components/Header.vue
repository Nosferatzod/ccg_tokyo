<template>
  <header class="header">
  </header>
</template>

<script>
export default {
  name: 'AppHeader' // Mudança aqui: Nome do componente agora é "AppHeader"
}
</script>

<style scoped>
.header {
  background-color: #222;
  padding: 20px;
  text-align: center;
  color: #fff;
  font-family: 'Arial', sans-serif;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.5);
}
.header h1 {
  font-size: 3rem;
  letter-spacing: 2px;
  text-transform: uppercase;
}
</style>
