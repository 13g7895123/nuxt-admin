<template>
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
    