<!-- TEMPLATE -->
<template>
    <div class="signup container">
        <main class="py-3">
            <FormRegister />
        </main>
    </div>
</template>

<!-- SCRIPT -->
<script>
import FormRegister from '@/components/FormRegister.vue'

export default {
    name: 'SignUpView',
    components: {
        FormRegister
    }
}
</script>

<!-- STYLE -->
<style scoped lang="scss"></style>
