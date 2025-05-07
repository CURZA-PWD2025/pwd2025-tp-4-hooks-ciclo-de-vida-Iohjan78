<template>
  <div class="container">
    <h2>Dimensiones:</h2>
    <h3>{{ altura }} px. x {{ ancho }} px.</h3>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from "vue";

const altura = ref(window.innerHeight);
const ancho = ref(window.innerWidth);

function leerValores() {
  altura.value = window.innerHeight;
  ancho.value = window.innerWidth;
}

onMounted(() => {
  window.addEventListener("resize", leerValores);
});

onUnmounted(() => {
  window.removeEventListener("resize", leerValores);
});
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  padding: 1rem;
}
</style>
