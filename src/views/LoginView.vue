<!-- TEMPLATE -->
<template>
    <div class="login container">
        <main class="py-3">
            <FormLogin />
        </main>
    </div>
</template>

<!-- SCRIPT -->
<script>
import FormLogin from '@/components/FormLogin.vue'

export default {
    name: 'LoginView',
    components: {
        FormLogin
    }
}
</script>

<!-- STYLE -->
<style scoped lang="scss"></style>
