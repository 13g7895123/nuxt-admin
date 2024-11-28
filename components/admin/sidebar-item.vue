<template>
    <NuxtLink v-if="(isSubItem == false)" :to="path" class="flex items-center py-3 px-3 hover:bg-white hover:text-[#555] hover:shadow-glow shadow-white cursor-pointer rounded-md transition duration-300 ease-in-out">
        <Icon class="w-10 text-lg" :name="icon"></Icon>
        <label>{{ name }}</label>
    </NuxtLink>
    <NuxtLink v-else :to="path" class="flex items-center py-3 px-3 hover:bg-white hover:text-[#555] hover:shadow-glow shadow-white cursor-pointer rounded-md transition duration-300 ease-in-out">
        <Icon class="w-10 ml-5 text-xs font-bold" :name="'ic:outline-circle'"></Icon>
        <label>{{ name }}</label>
    </NuxtLink>
</template>
<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    path: String,
    name: String,
    icon: String,
    isSubItem: {
        type: Boolean,
        default: false,
    }
});
</script>