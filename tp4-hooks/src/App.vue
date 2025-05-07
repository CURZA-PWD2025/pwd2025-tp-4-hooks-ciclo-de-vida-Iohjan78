<script setup lang="ts">
import Lista from "./components/Lista.vue";
import Tareas from "./components/Tareas.vue";
import DimensionComponente from "./components/DimensionComponente.vue";
import { ref, computed } from "vue";

const componenteId = ref("Lista");

const components = {
  Lista,
  Tareas,
  DimensionComponente,
};

const selectedComponent = computed(() => components[componenteId.value]);
</script>

<template>
  <div class="barra-select">
    <div class="selector-wrapper">
      <select class="selector" v-model="componenteId">
        <option value="Lista">Lista</option>
        <option value="Tareas">Tareas</option>
        <option value="DimensionComponente">Dimensiones</option>
      </select>
    </div>
  </div>
  <component :is="selectedComponent" />
</template>

<style scoped>
.barra-select {
  width: 100%;
  background-color: rgb(41, 41, 41); /* fondo completo */
  padding: 20px 0;
}

.selector-wrapper {
  width: 100%;
  display: flex;
  justify-content: center; /* centra horizontalmente */
}

.selector {
  width: 200px; /* select más pequeño */
  padding: 10px;
  font-size: 16px;
  background-color: #f0f0f0;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}
</style>
