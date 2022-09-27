<template>
    <div>
        <Navbar />

        <main class="py-9">
            <div class="container mx-auto max-w-5xl">
                <nuxt />
            </div>
        </main>
    </div>
</template>

<script>
    import Navbar from '@/components/Navbar'

    export default {
        components: {
            Navbar
        }
    }
</script>