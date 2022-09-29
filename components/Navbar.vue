<!-- This example requires Tailwind CSS v2.0+ -->
<template>
    <div as="nav" class="bg-gray-800">
      <div class="mx-auto max-w-7xl px-2">
        <div class="flex flex-1 items-center h-16">
            <div class="flex space-x-4">
                <nuxt-link
                    v-for="item in navigation" 
                    :key="item.name"
                    :to="item.href"
                    exact
                    no-prefetch
                    active-class="bg-gray-900 text-white"
                    class="text-gray-300 hover:bg-gray-700 hover:text-white 
                        px-3 py-2 rounded-md text-sm font-medium" 
                >
                    {{ item.name }}
                </nuxt-link>
                <nuxt-link
                    v-if="!hasToken"
                    to="/login"
                    no-prefetch
                    class="text-gray-300 hover:bg-gray-700 hover:text-white 
                        px-3 py-2 rounded-md text-sm font-medium"
                >
                    Login
                </nuxt-link>
                <a 
                    v-else
                    @click.prevent="logout" 
                    href="#"
                    class="text-gray-300 hover:bg-gray-700 hover:text-white 
                        px-3 py-2 rounded-md text-sm font-medium"
                >
                    Logout
                </a>
            </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>  
    export default {
        data() {
            return {
                navigation: [
                    { name: 'Home', href: '/' },
                    { name: 'About', href: '/about' },
                    { name: 'Users', href: '/users' },
                ]
            }
        },
        computed: {
            hasToken() {
                return this.$store.getters.hasToken
            }
        },
        methods: {
            logout() {
                this.$store.dispatch('logout')
                this.$router.push('/login')
            }
        }
    }
  </script>