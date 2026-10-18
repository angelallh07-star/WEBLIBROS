<template>
  <div class="view">
    <h2>Catálogo de Libros</h2>

    <!-- Estados requeridos por la rúbrica -->
    <div v-if="cargando">⏳ Cargando libros desde Firestore...</div>
    <div v-else-if="error" style="color: red;">❌ Error al cargar: {{ error }}</div>
    <div v-else-if="libros.length === 0">📭 No hay libros disponibles.</div>

    <!-- Lista de libros (Padre pasa datos a Hijo mediante props) -->
    <div v-else>
      <LibroCard 
        v-for="item in libros" 
        :key="item.id" 
        :libro="item" 
      />
    </div>
  </div>
</template>

<script>
import { collection, getDocs } from "firebase/firestore";
import { db } from "@/firebase";
import LibroCard from "@/components/LibroCard.vue";

export default {
  name: "CatalogoView",
  components: { LibroCard },
  data() {
    return {
      libros: [],
      cargando: true,
      error: null
    };
  },
  async mounted() {
    try {
      const querySnapshot = await getDocs(collection(db, "libros"));
      const docs = [];
      querySnapshot.forEach((doc) => {
        docs.push({ id: doc.id, ...doc.data() });
      });
      this.libros = docs;
    } catch (e) {
      this.error = e.message;
    } finally {
      this.cargando = false;
    }
  }
};
</script>
<style scoped> .view { padding: 20px; } </style>