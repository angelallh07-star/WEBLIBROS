<template>
  <header class="header">
    <h1>📚 Mi Biblioteca Dinámica</h1>
    <nav>
      <RouterLink to="/">Inicio</RouterLink> |
      <RouterLink to="/catalogo">Catálogo</RouterLink> |
      <RouterLink to="/contacto">Contacto</RouterLink>
    </nav>
  </header>
</template>

<style scoped>
.header {
  background-color: #2c3e50;
  color: white;
  padding: 1rem;
  text-align: center;
}
nav a {
  color: #42b983;
  margin: 0 10px;
  text-decoration: none;
  font-weight: bold;
}
nav a.router-link-exact-active {
  color: #ffffff;
  text-decoration: underline;
}
</style>