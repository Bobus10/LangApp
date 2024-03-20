<script setup>
import { Link } from '@inertiajs/vue3';
import ResponsiveNavLink from './ResponsiveNavLink.vue';

defineProps({
    showingNavigationDropdown: {
        type: Boolean,
        required: true,
    },
    canLogin: {
        type: Boolean,
        default: true
    },
    canRegister: {
        type: Boolean,
        default: true
    },
    navlinks: {
        type: Array,
    }
});
</script>

<template>
    <div
        :class="{ block: showingNavigationDropdown, hidden: !showingNavigationDropdown }"
        class="sm:hidden"
    >
        <div v-if="canLogin">
            <template v-if="$page.props.auth.user">
                <div v-for="navlink in navlinks" class="pt-2 pb-3 space-y-1">
                    <ResponsiveNavLink :href="route(navlink.route)" :active="route().current(navlink.route)">
                        {{ navlink.label }}
                    </ResponsiveNavLink>
                </div>

                <!-- Responsive Settings Options -->
                <div class="pt-4 pb-1 border-t border-gray-200">
                    <div class="px-4">
                        <div class="font-medium text-base text-gray-800">
                            {{ $page.props.auth.user.name }}
                        </div>
                        <div class="font-medium text-sm text-gray-500">
                            {{ $page.props.auth.user.email }}
                        </div>
                    </div>

                    <div class="mt-3 space-y-1">
                        <ResponsiveNavLink :href="route('profile.edit')">
                            Profile
                        </ResponsiveNavLink>
                        <ResponsiveNavLink :href="route('logout')" method="post" as="button">
                            Log Out
                        </ResponsiveNavLink>
                    </div>
                </div>
            </template>

            <template v-else>
                <div class="flex flex-col text-center p-3">
                    <Link
                        :href="route('login')"
                        class="font-semibold text-gray-600 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white focus:outline focus:outline-2 focus:rounded-sm focus:outline-red-500">
                        Log in
                    </Link>

                    <Link
                        v-if="canRegister"
                        :href="route('register')"
                        class="font-semibold text-gray-600 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white focus:outline focus:outline-2 focus:rounded-sm focus:outline-red-500"
                    >
                        Register
                    </Link>
                </div>
            </template>
        </div>
    </div>
</template>
