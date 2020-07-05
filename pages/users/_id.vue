<template>
    <section>
        <h1>User: {{user.name}}</h1>
        <hr>
        <h3>Email: {{user.email}}</h3>
        <p>Phone: {{user.phone}}</p>
    </section>
</template>

<script>
export default {
    validate({params}) {
        console.log('validate');
        return /^\d+$/.test(params.id);
    },
    async asyncData({$axios, params}) {
        const user = await $axios.$get(`https://jsonplaceholder.typicode.com/users/${params.id}`);
        return {user}
    }
}
</script>