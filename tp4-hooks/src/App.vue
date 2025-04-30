<script setup lang="ts">
import Lista from "./components/Lista.vue";
import Tareas from "./components/Tareas.vue";
import DimensionComponente from "./components/DimensionComponente.vue";
import { ref } from "vue";

const selectedComponent = ref("dimension");
</script>

<template>
  <div class="container">
    <div class="selector">
      <select v-model="selectedComponent">
        <option value="lista">Lista</option>
        <option value="tareas">Tareas</option>
        <option value="dimension">Dimension de navegador</option>
      </select>
    </div>
    <div class="componente">
      <DimensionComponente v-if="selectedComponent === 'dimension'" />
      <Lista v-if="selectedComponent === 'lista'" />
      <Tareas v-if="selectedComponent === 'tareas'" />
    </div>
  </div>
</template>

<style scoped>


.selector {
  margin-bottom: 1.5rem;
}


.selector {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  padding: 0.5rem;
  background: rgb(255, 69, 69);
  z-index: 1000;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}



</style>
