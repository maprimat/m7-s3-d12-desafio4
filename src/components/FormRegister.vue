<!-- TEMPLATE -->
<template>
    <div class="row justify-content-center">
        <div class="col-12 col-md-8 py-3 w-50">
            <h1 class="fw-bold">Crea tu cuenta</h1>
            <hr>
            <form class="col-12" @submit.prevent="registerUser">
                <div class="form-floating mb-3">
                    <input type="text" class="form-control mt-3" id="floatingName"
                        placeholder="Escriba su nombre y apellido" v-model="name" required>
                    <label for="floatingName" class="mb-5">Nombre y apellido</label>
                </div>
                <div class="form-floating mb-3">
                    <input type="email" class="form-control mt-3" id="floatingEmail" placeholder="name@example.com"
                        v-model="email" required>
                    <label for="floatingEmail" class="mb-5">Correo electrónico</label>
                </div>
                <div class="input-group mb-3">
                    <span class="input-group-text">@</span>
                    <div class="form-floating">
                        <input type="text" class="form-control" id="floatingUsername" placeholder="Nickname"
                            v-model="username" required>
                        <label for="floatingUsername">Nombre de usuario</label>
                    </div>
                </div>
                <div class="form-floating mb-3">
                    <input type="password" class="form-control" id="password" placeholder="Escriba su contraseña"
                        v-model="password" required>
                    <label for="password">Contraseña</label>
                </div>
                <div class="form-floating mb-3">
                    <input type="password" class="form-control" id="replyPassword"
                        placeholder="Por favor escriba su contraseña nuevamente" v-model="replyPassword" required>
                    <label for="replyPassword">Repita contraseña</label>
                </div>
                <div class="mb-3">
                    <button type="submit" class="btn btn-primary text-white p-3" :disabled="loadingRegister">Registrarse</button>
                </div>
            </form>
        </div>
    </div>
</template>

<!-- SCRIPT -->
<script>

import { auth, createUserWithEmailAndPassword } from '@/auth'

export default {
    name: 'FormRegister',
    data() {
        return {
            name: '',
            email: '',
            username: '',
            password: '',
            replyPassword: '',
            loadingRegister: false
        }
    },
    methods: {
        async registerUser() {
            try {
                if (!this.nombre, !this.email, !this.username, !this.password, !this.replyPassword) {
                    return alert("¡Debes completar todos los campos!");
                }

                if (this.password != this.replyPassword) {
                    return alert("¡Las contraseñas no coinciden! Intenta nuevamente")
                }

                this.loadingRegister = true;
                const userCredentials = await createUserWithEmailAndPassword(auth, this.email, this.password);
                console.log(userCredentials);
                alert("¡Usuario registrado exitosamente!");
                this.$router.push("/user");
                this.loadingRegister = false;
                this.$router.push("/");
            } catch (error) {
                console.log(error);
                alert("Ha fallado el registro. Intenta nuevamente");
            }
        }
    }
}
</script>

<!-- STYLE -->
<style scoped lang="scss"></style>