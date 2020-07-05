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
    async fetch({store}) {
        if (!store.getters['users/users'].length) {
            await store.dispatch('users/fetchUsers')
        }
    },
    computed: {
        users() {
            return this.$store.getters['users/users'];
        }
    },
    methods: {
        openUser(id) {
            this.$router.push(`/users/${id}`)
        }
    }
}
</script>