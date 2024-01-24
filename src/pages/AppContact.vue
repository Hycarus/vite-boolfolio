<template>
    <div class="container">
        <h1 class="text-white">Contact Us</h1>
        <ContactForm></ContactForm>
    </div>
</template>

<script>
import ContactForm from '../components/ContactForm.vue'
export default {
    name: 'AppContact',
    components: {
        ContactForm
    }
}
</script>

<style lang="scss" scoped></style>