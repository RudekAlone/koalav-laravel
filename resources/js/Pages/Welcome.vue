<script setup>
import { Head, Link } from "@inertiajs/vue3";

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
    laravelVersion: {
        type: String,
        required: true,
    },
    phpVersion: {
        type: String,
        required: true,
    },
});
</script>

<template>
    <Head title="Koala V" />
    <header
        class="h-20 bg-gradient-to-r from-teal-900 from-15% via-slate-900 to-pink-950 to-85% items-center flex justify-center"
    >
        <img src="/favicon.png" alt="" />
        <h1
            class="h-12 w-48 font-LuckiestGuy text-5xl text-center font-outline-4 text-gray-400 bg-gradient-to-b from-cyan-500 to-fuchsia-600"
        >
            Koala V
        </h1>
        <div class="">
            <div
                v-if="canLogin"
                class="sm:fixed sm:top-0 sm:right-0 p-6 text-right"
            >
                <Link
                    v-if="$page.props.auth.user"
                    :href="route('dashboard')"
                    class="font-semibold text-gray-600 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white focus:outline focus:outline-2 focus:rounded-sm focus:outline-red-500"
                    >Dashboard</Link
                >

                <template v-else>
                    <Link
                        :href="route('login')"
                        class="font-semibold text-gray-600 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white focus:outline focus:outline-2 focus:rounded-sm focus:outline-red-500"
                        >Log in</Link
                    >

                    <Link
                        v-if="canRegister"
                        :href="route('register')"
                        class="ml-4 font-semibold text-gray-600 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white focus:outline focus:outline-2 focus:rounded-sm focus:outline-red-500"
                        >Register</Link
                    >
                </template>
            </div>
        </div>
    </header>
    <main class="bg-slate-800 h-max text-gray-300">CODE</main>
</template>

<style></style>
