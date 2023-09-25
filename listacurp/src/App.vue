<template>
  <div>
    <h1>Bienvenido</h1>
    <AgregarUsuarios></AgregarUsuarios>
    <ListaUsuario></ListaUsuario>
  </div>
</template>

<script lang="ts" setup>
import AgregarUsuarios from './components/AgregarUsuarios.vue'
import ListaUsuario from './components/ListaUsuario.vue'
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
