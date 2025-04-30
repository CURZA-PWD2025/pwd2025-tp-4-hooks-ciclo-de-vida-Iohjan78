<template>
  <div class="inputContenedor">
    <input
      type="text"
      class="inputTareas"
      v-model="nuevaTarea"
      @keyup.enter="agregarTarea"
      @focus="inputTocado = true"
    />
  </div>
  <div v-for="(tarea, index) in tareas" :key="index" :class="{ verde: index < tareasPrevias}">
    {{ tarea }}
  </div>
</template>

<script setup lang="ts">
import { ref, onBeforeUpdate, onUpdated } from "vue";

//array con las tareas
const tareas = ref(["tarea 1", "tarea 2"]);
//valor del input
const nuevaTarea = ref("");
//indica que la variante inputtocado esta en falso
const inputTocado= ref(false);
//y una variente contador en 0
let tareasPrevias=0;

//si hay algo escrito, lo limpia de los espacios, lo pushea a tareas y limpia el area para volver a escribir
function agregarTarea() {
  if (nuevaTarea.value.trim()) {
    tareasPrevias = tareas.value.length; // pinta las ya existentes
    tareas.value.push(nuevaTarea.value.trim()); //agrega a tareas una nueva tarea
    nuevaTarea.value = ""; //deja en blanco los espacios
  }
}

onBeforeUpdate(() => {
  if (inputTocado.value) {
    
    console.log("lista aun no modificada");
  }
});

onUpdated(() => {
  console.log("lista modificada");
});
</script>

<style scoped>
.verde {
  color: green;

  padding: 0.2rem 0.2rem;
  width: fit-content;
  margin: 0 auto;
}
  
.inputContenedor {
  max-width: 600px;
  margin: 2rem auto;
  padding: 0 1rem;
}

.inputTareas {
  width: 100%;
  padding: 1rem;
  box-sizing: border-box;
}
.nuevaTarea {
    padding: 0.5rem;
    width: 33%;
}

</style>
