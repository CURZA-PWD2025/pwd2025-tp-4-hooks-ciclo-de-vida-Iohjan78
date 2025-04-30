<template>
  <div class="container">
    <div class="card" v-for="value in lista">
      <h3>Profesion: {{ value.nombre }}</h3>
      <p> Descripcion: {{ value.descripcion }}</p>
    </div>
  </div>
</template>

<script setup lang="ts">
import { onMounted, ref } from "vue";
import { profesiones } from "../resource/profesiones";

const lista = ref([]);

onMounted(() => {
  setTimeout(() => {
    lista.value = profesiones;
  }, 3000);
});
</script>

<style scoped>
.container {
    gap: 0.2rem;
    padding: 0.5rem;
}

h3 {
    background-color: rgb(58, 111, 255);
    padding: 1.5rem;
}
.card {
    background-color: rgb(204, 211, 253);
    padding: 0.1rem 0.1rem;
    border-radius: 4px;
    border: 1px solid #ddd;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

</style>
