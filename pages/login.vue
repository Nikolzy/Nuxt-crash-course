<template>
    <section>
        <div v-if="$route.query.message" class="alert alert-danger mb-3">
            Need login first
        </div>
        <form action="" @submit.prevent="handleSubmit">
            <h1>Login page</h1>
            <div class="form-group">
                <input type="text" class="form-control">
            </div>
            
            <p>
                <nuxt-link to="/">Home page</nuxt-link>
            </p>

            <button class="btn btn-primary" type="submit">Login</button>
        </form>
    </section>
</template>

<script>
export default {
    layout: 'empty',
    methods: {
        handleSubmit() {
            this.$store.dispatch('login');
            this.$router.push('/');
        }
    }
}
</script>

<style scoped>
    section {
        max-width: 500px;
        width: 100%;
        margin: 0 auto;
        padding: 0 20px;
    }
</style>