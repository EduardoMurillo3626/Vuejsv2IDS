<template>
    <div class="container">
    <p>Email</p>
    <input type="text" v-model="email" />
    <p>Contraseña</p>
    <input type="password" v-model="pass" />
    <button @click="acceder">Acceder</button>

    <!-- Mostrar la tabla de usuarios después de iniciar sesión -->
    <table v-if="mostrarTabla">
        <thead>
        <tr>
            <th>I#</th>
            <th>Nombre</th>
            <th>username</th>
            <th>email</th>
            <th>phone</th>
            <th>website</th>
            <th>Action</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="user in usuarios" :key="user.id">
            <td>{{ user.id }}</td>
            <td>{{ user.name }}</td>
            <td>{{ user.username }}</td>
            <td>{{ user.email }}</td>
            <td>{{ user.phone }}</td>
            <td>{{ user.website }}</td>
            <td><button>Edit</button>
            <button>delet</button></td>
        </tr>
        </tbody>
    </table>
    </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import usersData from "../components/user.json"; // Importar datos de usuarios desde el archivo JSON

const email = ref("");
const pass = ref("");
const mostrarTabla = ref(false); // Variable para controlar la visibilidad de la tabla
const usuarios = ref([]); // Lista para almacenar los datos de usuario

const acceder = () => {
    let login = false;

    usersData.forEach((user: any) => { // Se supone que los datos de usuario tienen una propiedad "id"
    if (email.value === user.email && pass.value === user.password) {
        alert("¡Bienvenido!");
        login = true;

        // Si se inicia sesión correctamente, asigna los datos de usuarios y muestra la tabla
        usuarios.value = usersData;
        mostrarTabla.value = true;
    }
    });

    if (!login) {
    alert("Usuario o contraseña incorrectos");
    }
};
</script>
