<template>
  <div>
    <form action="">
      <fieldset>
        <legend>Nombre</legend>
        <input type="text" v-model="username">
      </fieldset>
      <fieldset>
        <legend>Apellido</legend>
        <input type="text" v-model="lastname">
      </fieldset>
      <!-- Botón para guardar los datos ingresados -->
      <button @click="save">Guardar</button>
    </form>
    
    <!-- Lista para mostrar los nombres y apellidos guardados -->
    <ul>
      <li v-for="persona in personas" :key="persona.id">
        <!-- Muestra el nombre y el apellido de cada persona -->
        {{ persona.name }} {{ persona.lastname }}
      </li>
    </ul>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';

// Variables reactivas para almacenar datos
const username = ref('');
const lastname = ref('');
const personas = ref<{ id: number; name: string; lastname: string }[]>([]);

// Función para guardar los datos ingresados en la lista 'personas'
const save = () => {
  // Agrega un nuevo objeto a 'personas' con un ID único, nombre y apellido
  personas.value.push({ id: personas.value.length + 1, name: username.value, lastname: lastname.value });
  
  // Reinicia los campos de nombre y apellido
  username.value = '';
  lastname.value = '';
};
</script>