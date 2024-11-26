<template>
    <div class="flex items-center py-2 px-3 hover:bg-white hover:text-[#555] cursor-pointer rounded-md transition duration-300 ease-in-out">
        <Icon class="w-10 text-lg" :name="icon"></Icon>
        <NuxtLink :to="path" class="hover:text-gray-300">{{ name }}</NuxtLink>
    </div>
</template>
<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    path: String,
    name: String,
    icon: String,
});
</script>