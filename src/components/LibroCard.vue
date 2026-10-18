<template>
  <div class="card">
    <h3>{{ libro.titulo }}</h3>
    <p><strong>Autor:</strong> {{ libro.autor }}</p>
    <p><strong>Año:</strong> {{ libro.anio }}</p>
    <p>{{ libro.descripcion }}</p>
  </div>
</template>

<script>
export default {
  name: 'LibroCard',
  props: {
    // Declaración estricta de la prop que recibe del componente padre
    libro: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.card {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 15px;
  margin: 10px 0;
  background-color: #fafafa;
}
</style>