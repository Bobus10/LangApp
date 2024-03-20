<script setup>
import Navigation from '@/Components/navigation/Navigation.vue';

</script>

<template>
    <div class="">
        <Navigation />
        <!-- Page Heading -->
        <header class="bg-white shadow" v-if="$slots.header">
            <div class="max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8">
                <slot name="header" />
            </div>
        </header>
        <main>
            <slot />
        </main>
    </div>
</template>
