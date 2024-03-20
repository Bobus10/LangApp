<script setup>
import { Head } from '@inertiajs/vue3';
import AppLayout from '@/Layouts/AppLayout.vue';

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
});
</script>

<template>
    <Head title="Welcome" />

    <AppLayout>
        <template #header>
            Welcome
        </template>
        <div>
            Welcome
        </div>
    </AppLayout>

</template>
