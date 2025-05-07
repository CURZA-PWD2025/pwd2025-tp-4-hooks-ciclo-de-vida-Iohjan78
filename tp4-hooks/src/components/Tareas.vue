<template>
  <div class="container">
    <input type="text" v-model="input" @keyup.enter="agregarTarea" />
    <ul>
      <li v-for="item in lista_tareas" ref="li">
        {{ item }}
      </li>
    </ul>
  </div>

  <!--DEJO COMENTADO CONSTANCIA DEL CAOS QUE NO PROSPERO PARA REALIZAR ESTE PUNTO-->

  <!-- <div class="inputContenedor">
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
  </div>-->
</template>

<script setup lang="ts">
import { ref, onBeforeUpdate, onUpdated } from "vue";

const input = ref("");
const li = ref(null);
const lista_tareas = ref(["tarea1", "tarea2"]);
const agregarTarea = () => {
  if (input.value) {
    lista_tareas.value.push(input.value);
    input.value = "";
  }
};

onBeforeUpdate(() => {
  console.log("antes de modificar la lista");
  li.value.forEach((li) => {
    li.style.color = "green";
  });
});

onUpdated(() => {
  console.log("lista modificada");
});

/*
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
    tareas.value.push(nuevaTarea.value.trim());
    nuevaTarea.value = "";
    tareasPrevias = 0; 
  }
}

watch(nuevaTarea, (valor) => {
  if (valor.trim().length > 0 && tareasPrevias === 0) {
    tareasPrevias = tareas.value.length;
  }
});


onBeforeUpdate(() => {
  if (inputTocado.value) {
    
    console.log("lista aun no modificada");
  }
});

onUpdated(() => {
  console.log("lista modificada");
});
*/
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
