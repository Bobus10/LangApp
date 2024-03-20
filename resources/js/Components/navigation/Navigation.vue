<script setup lang="ts">
import ApplicationLogo from '@/Components/ApplicationLogo.vue';
import NavLink from './NavLink.vue';
import ResponsiveNavigationMenu from './ResponsiveNavigationMenu.vue';
import Hamburger from './Hamburger.vue';
import LoginOrRegister from './LoginOrRegister.vue';
import { Ref, ref } from 'vue';

let showingNavigationDropdown: Ref<boolean> = ref(false);

const handleToggleDropdown = () => {
    showingNavigationDropdown.value = !showingNavigationDropdown.value;
};

interface NavLink {
    route: string;
    label: string;
};

const navlinks: NavLink[] = [
    {
        route: 'welcome',
        label: 'Welcome'
    },
    {
        route: 'dashboard',
        label: 'Dashboard'
    }
];
</script>

<template>
    <nav class="bg-white border-b border-gray-100">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <!-- Primary Navigation Menu -->
            <div class="flex justify-between h-16">
                <div class="flex">
                    <div class="shrink-0 flex items-center">
                        <Link :href="route('welcome')">
                            <ApplicationLogo
                                class="block h-9 w-auto fill-current text-gray-800"
                            />
                        </Link>
                    </div>
                    <div v-for="navlink in navlinks" class="hidden space-x-8 sm:-my-px sm:ms-10 sm:flex">
                        <NavLink :href="route(navlink.route)" :active="route().current(navlink.route)">
                            {{ navlink.label }}
                        </NavLink>
                    </div>
                </div>
                <div class="hidden sm:flex sm:items-center sm:ms-6">
                    <LoginOrRegister />
                </div>
                <div class="-me-2 flex items-center sm:hidden">
                    <Hamburger @toggleDropdown="handleToggleDropdown" :showingNavigationDropdown="showingNavigationDropdown" />
                </div>
            </div>
        </div>

        <ResponsiveNavigationMenu :showingNavigationDropdown="showingNavigationDropdown" :navlinks="navlinks"/>
    </nav>
</template>
