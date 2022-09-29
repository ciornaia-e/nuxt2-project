<template>
    <section class="mx-auto max-w-xl">
        <h1 class="text-center text-4xl mb-10">Login page</h1>

        <div 
            v-if="$route.query.message"
            class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded mb-3" 
            role="alert"
        >
            <span>Need login first</span>
        </div>

        <form @submit.prevent="onSubmit" class="bg-gray-50">
            <div class="px-4 py-5">
                <div class="grid grid-cols-6 gap-6">
                    <div class="col-span-6">
                        <label 
                            for="first-name" 
                            class="block text-sm font-medium text-gray-700"
                        >
                            First name
                        </label>
                        <input 
                            type="text" 
                            name="first-name" 
                            id="first-name" 
                            autocomplete="given-name" 
                            class="mt-1 block w-full py-1 px-2 rounded-md border border-gray-300 focus:border-indigo-500 focus:ring-indigo-500" 
                        />
                    </div>

                    <div class="col-span-6">
                        <label 
                            for="email-address" 
                            class="block text-sm font-medium text-gray-700"
                        >
                            Email address
                        </label>
                        <input 
                            type="text" 
                            name="email-address" 
                            id="email-address" 
                            autocomplete="email" 
                            class="mt-1 block w-full py-1 px-2 rounded-md border border-gray-300 focus:border-indigo-500 focus:ring-indigo-500" 
                        />
                    </div>    
                </div>
            </div>
            <div class="px-4 py-3 text-right">
                <button 
                    type="submit" 
                    class="inline-flex justify-center rounded-md border border-transparent bg-indigo-600 py-2 px-4 text-sm font-medium text-white hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2"
                >
                    Login
                </button>
            </div>
        </form>
        <p class="mt-3">
            <nuxt-link to="/" class="text-indigo-600">To home page</nuxt-link>   
        </p>
    </section>
</template>

<script>
    export default {
        layout: 'empty',
        methods: {
            onSubmit() {
                this.$store.dispatch('login')
                this.$router.push('/')
            }
        }
    }
</script>