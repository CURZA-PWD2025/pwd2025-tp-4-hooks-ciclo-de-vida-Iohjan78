<template>
  <div class="container">
    <div v-if="cargando" class="loading">
      <img src="/loading.gif" alt="Cargando..." />
    </div>
    <div v-else>
      <div class="card" v-for="value in lista" :key="value.nombre">
        <h3>Profesión: {{ value.nombre }}</h3>
        <p>Descripción: {{ value.descripcion }}</p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { onMounted, ref } from "vue";
import { profesiones } from "../resource/profesiones";

const lista = ref([]);
const cargando = ref(true);

onMounted(() => {
  setTimeout(() => {
    lista.value = profesiones;
    cargando.value = false;
  }, 3000);
});
</script>

<style scoped>
.container {
  gap: 0.2rem;
  padding: 0.5rem;
  text-align: center;
}
h3 {
  background-color: rgb(148, 177, 255);
  padding: 1.5rem;
}
.card {
  background-color: rgb(204, 211, 253);
  padding: 0.1rem 0.1rem;
  border-radius: 4px;
  border: 1px solid #ddd;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}
.loading img {
  width: 60px;
  height: 60px;
  margin-top: 2rem;
}
</style>
