<template>
    <section>
        <h1 class="text-center text-4xl mb-10">Users page</h1>

        <ul>
            <li 
                v-for="user in users" 
                :key="user.id"
                class="mb-2"
            >
                <span class="text-slate-700">User </span>
                <a 
                    @click.prevent="openUser(user)"
                    href="#"
                    class="text-indigo-600"
                >
                    {{ user.name }}
                </a>
            </li>
        </ul>
    </section>
</template>

<script>
    export default {
        async asyncData({ $axios }) {
            const users = await $axios.$get('https://jsonplaceholder.typicode.com/users')
            return { users }
        },
        data() {
            return {
                users: []
            }
        },
        methods: {
            openUser(user) {
                this.$router.push(`/users/${user.id}`)
            }
        }
    }
</script>