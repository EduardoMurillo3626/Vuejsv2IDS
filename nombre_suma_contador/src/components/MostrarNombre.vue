<template>
    <div class="mostrar_nombre">
        <h1>Hola soy {{nombre}}</h1>
        <input type="text" v-model="nombre">
    </div>
</template>

<script lang="ts" setup>
    import {ref} from 'vue'

    const nombre = ref('')
</script>