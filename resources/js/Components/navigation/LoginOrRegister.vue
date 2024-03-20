<script setup>
import { Link } from '@inertiajs/vue3';
import UserSettingsDropDown from './UserSettingsDropDown.vue';

defineProps({
    canLogin: {
        type: Boolean,
        default: true
    },
    canRegister: {
        type: Boolean,
        default: true
    },
});
</script>

<template>
    <div v-if="canLogin" class="sm:fixed sm:top-0 sm:right-0 p-6 text-end">
        <!-- Dropdown user menu -->
        <template v-if="$page.props.auth.user">
            <UserSettingsDropDown />
        </template>

        <template v-else>
            <Link
                :href="route('login')"
                class="font-semibold text-gray-600 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white focus:outline focus:outline-2 focus:rounded-sm focus:outline-red-500">
                Log in
            </Link>

            <Link
                v-if="canRegister"
                :href="route('register')"
                class="ms-4 font-semibold text-gray-600 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white focus:outline focus:outline-2 focus:rounded-sm focus:outline-red-500"
            >
                Register
            </Link>
        </template>
    </div>
</template>
