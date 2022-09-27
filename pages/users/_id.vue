<template>
    <section>
        <!-- <h1 class="text-center text-4xl mb-10">User {{ $route.params.id }}</h1> -->
        <h1 class="text-4xl mb-10">{{ user.name }}</h1>
        <hr />
        <div class="mt-5">
            <div class="inline-block bg-slate-100 p-2 rounded border border-slate-300">
                <span class="text-slate-700">User email: </span>
                <span>{{ user.email }}</span>
            </div>
        </div>
    </section>
</template>

<script>
    export default {
        validate({ params }) {
            return /^\d+$/.test(params.id)
        },
        async asyncData({ $axios, params }) {
            const user = await $axios.$get(`https://jsonplaceholder.typicode.com/users/${params.id}`)
            return { user }
        },
    }
</script>