<!-- TEMPLATE -->
<template>
    <nav class="navbar bg-dark navbar-expand-lg py-4 px-5 text-ligth" data-bs-theme="dark">
        <div class="container">
            <a class="navbar-brand" href="/"><i class="fa-solid fa-user-secret mx-2"></i>Control de Usuarios</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
                aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav ms-auto">
                    <li class="nav-item">
                        <router-link to="/" class="nav-link"><i class="fa-solid fa-house px-2"></i>Inicio</router-link>
                    </li>
                    <li class="nav-item">
                        <router-link to="/user" class="nav-link" v-if="user"><i class="fa-solid fa-user px-2"></i>Mi perfil</router-link>
                    </li>
                    <li class="nav-item">
                        <router-link to="/login" class="nav-link" @click.prevent="logout" v-if="user"><i
                                class="fa-solid fa-right-from-bracket px-2"></i>Cerrar Sesión</router-link>
                    </li>
                    <li class="nav-item">
                        <router-link to="/sign-up" class="nav-link" v-if="!user"><i class="fa-solid fa-key px-2"></i>Registrarse</router-link>
                    </li>
                    <li class="nav-item">
                        <router-link to="/login" class="nav-link" v-if="!user"><i
                                class="fa-solid fa-user-lock px-2"></i>Iniciar Sesión</router-link>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</template>

<!-- SCRIPT -->
<script>
import { auth, signOut } from '@/auth'
import { mapState } from 'vuex';

export default {
    name: "NavbarComp",
    components: {
    },
    computed: {
        ...mapState(["user"]),
    },
    methods: {
        async logout() {
            try {
                await signOut(auth);
                alert("¡Haz cerrado sesión correctamente!");
                this.$router.push("/");

            } catch (error) {
                console.log(error);
                alert("No se pudo cerrar la sesión. Intenta nuevamente");
            }
        }
    }
}
</script>

<!-- STYLE -->
<style scoped lang="scss"></style>