<template>
    <AdminDatatable :tableName="'User List'" :headers="headers" :items="items">
        <template #action-buttons>
            <div class="flex gap-1">
                <NuxtLink 
                to="/user/edit"
                class="flex items-center px-3 py-1 border-2 border-blue-400 hover:border-transparent hover:bg-blue-200 rounded-md cursor-pointer group">
                    <Icon class="text-base text-blue-200 group-hover:text-blue-500" :name="'fluent-emoji-high-contrast:plus'"></Icon>
                    <span class="ml-2 text-blue-200 group-hover:text-blue-500">New Data</span>
                </NuxtLink>
                <div class="flex items-center px-3 py-1 border-2 border-red-400 hover:border-transparent hover:bg-red-200 rounded-md cursor-pointer group">
                    <Icon class="text-lg text-red-200 group-hover:text-red-500" :name="'mynaui:trash'"></Icon>
                    <span class="ml-2 text-red-200 group-hover:text-red-500">Batch Delete Data</span>
                </div>
            </div>
        </template>
        <template #action="{ item }">
        <!-- <div class="flex justify-center"> -->
            <div
            @click="console.log(item)"
            class="flex justify-center items-center p-2 border-2 border-blue-200 hover:bg-blue-200 rounded-full cursor-pointer group">
            <Icon class="text-blue-300 group-hover:text-blue-500 text-lg" :name="'formkit:list'"></Icon>
            </div>
            <div class="flex justify-center items-center p-2 border-2 border-green-200 hover:bg-green-200 rounded-full cursor-pointer group">
            <Icon class="text-green-300 group-hover:text-green-500 text-2xl" :name="'tdesign:edit'"></Icon>
            </div>
            <div class="flex justify-center items-center p-2 border-2 border-red-200 hover:bg-red-200 rounded-full cursor-pointer group">
            <Icon class="text-red-300 group-hover:text-red-500 text-2xl" :name="'mynaui:trash'"></Icon>
            </div>
        <!-- </div> -->
        </template>
    </AdminDatatable>
</template>
  
<script setup>
definePageMeta({
layout: 'admin',
});

import { ref, computed } from "vue";

const headers = ref([
    { label: "Name", key: "name" },
    { label: "Age", key: "age" },
    { label: "Country", key: "country" },

    { label: "Age", key: "age" },
    { label: "Age", key: "age" },
    { label: "Age", key: "age" },
    { label: "Age", key: "age" },
    { label: "Age", key: "age" },
    { label: "Age", key: "age" },
    { label: "Age", key: "age" },
    { label: "Action", key: "action", headerClass: "text-center", itemClass: "flex gap-1 justify-center" },
]);

const items = ref([
    { id: 1, name: "Alice", age: 25, country: "USA" },
    { id: 2, name: "Bob", age: 30, country: "Canada" },
    { id: 3, name: "Charlie", age: 35, country: "UK" },
    { id: 1, name: "Alice", age: 25, country: "USA" },
    { id: 2, name: "Bob", age: 30, country: "Canada" },
    { id: 3, name: "Charlie", age: 35, country: "UK" },
    { id: 1, name: "Alice", age: 25, country: "USA" },
    { id: 2, name: "Bob", age: 30, country: "Canada" },
    { id: 3, name: "Charlie", age: 35, country: "UK" },
]);

</script>
    