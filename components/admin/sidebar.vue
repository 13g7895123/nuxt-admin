<template>
    <!-- Sidebar -->
    <aside class="w-1/5 bg-[#1e1d22] text-white p-5">
        <h2 class="text-2xl text-center font-bold mb-6">Admin Panel</h2>
        <nav>
            <label class="px-3 text-lg text-gray-300">System</label>
            <ul class="mt-3">
                <li v-for="item in sidebarItems">
                    <AdminSidebarItem :path="item.path" :name="item.name" :icon="item.icon"/>
                </li>
            </ul>
        </nav>
    </aside>
</template>
<script setup>
import { ref } from 'vue';

const sidebarItems = ref([
    {
        name: 'Dashboard',
        path: '/',
        icon: 'fa6-solid:list',
    },
    {
        name: 'User',
        path: '/',
        icon: 'eva:people-fill',
    },
    {
        name: 'Setting',
        path: '/',
        icon: 'ic:sharp-settings',
    },
]);
</script>