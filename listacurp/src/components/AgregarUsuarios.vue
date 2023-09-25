<template>
    <div class="container">
        <h1>Agregar</h1>
        <p>Name</p>
        <input type="text" v-model="name">
        <p>Username</p>
        <input type="text" v-model="username">
        <p>Email</p>
        <input type="text" v-model="email">
        <p>Password</p>
        <input type="text" v-model="pass">
        <p>Phone</p>
        <input type="text" v-model="phone">
        <p>Website</p>
        <input type="text" v-model="website">
        <button @click="agregarUsuario">add</button>
    </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import usersData from "../components/user.json";
import fs from "fs"; // Módulo para manejar el sistema de archivos (Node.js)

const email = ref("");
const pass = ref("");
const name = ref("");
const username = ref("");
const phone = ref("");
const website = ref("");
const usuarios = ref(usersData);

const agregarUsuario = () => {
    // Crea un nuevo objeto de usuario con los campos necesarios
    const nuevoUsuario = {
        id: usuarios.value.length + 1, // Genera un nuevo ID (puedes ajustar esto según tu lógica)
        name: name.value,
        username: username.value,
        email: email.value,
        phone: phone.value,
        website: website.value,
        password: pass.value,
    };

    // Agrega el nuevo usuario al arreglo de usuarios
    usuarios.value.push(nuevoUsuario);

    // Guarda los datos actualizados en el archivo user.json
    const jsonData = JSON.stringify(usuarios.value, null, 4);
    fs.writeFileSync("user.json", jsonData, "utf8");

    // Limpia los campos del formulario después de agregar el usuario
    name.value = "";
    username.value = "";
    email.value = "";
    phone.value = "";
    website.value = "";
    pass.value = "";
};

</script>