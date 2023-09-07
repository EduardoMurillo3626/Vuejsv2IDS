<template>
    <div class="suma">
        <input type="text" v-model="numero1">
        <input type="text" v-model="numero2">
        <h2>El resultado es {{resultado}}</h2>
    </div>
</template>

<script lang="ts" setup>
    import { ref, watch } from 'vue';

const numero1 = ref(0);
const numero2 = ref(0);
const resultado = ref(0);

watch([numero1, numero2], () => {
    resultado.value = Number(numero1.value) + Number(numero2.value);
});
</script>