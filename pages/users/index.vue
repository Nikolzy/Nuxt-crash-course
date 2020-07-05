<template>
    <section>
        <h1>Users page</h1>

        <ul>
            <li v-for="user of users" :key="user.email">
                <a href="#" @click.prevent="openUser(user.id)">{{user.name}}</a>
            </li>
        </ul>
    </section>
</template>

<script>
export default {
    async asyncData({$axios}) {
        const users = await $axios.$get('https://jsonplaceholder.typicode.com/users');
        return {users}
    },
    data: () => ({
        users: []
    }),
    methods: {
        openUser(id) {
            this.$router.push(`/users/${id}`)
        }
    }
}
</script>