<template>
  <div class="bg-[#1e1d22] rounded-lg shadow-glow shadow-white">
    <div class="flex justify-between items-center px-5 py-5 border-b border-white">
      <!-- Title -->
      <label class="text-xl text-bold">Table Name</label>
      <!-- Buttons -->
      <div>
        <div class="flex items-center px-3 py-1 bg-blue-400 hover:bg-blue-500 rounded-md cursor-pointer">
          <Icon class="text-base" :name="'fluent-emoji-high-contrast:plus'"></Icon>
          <span class="ml-2">New Data</span>
        </div>
      </div>
    </div>
    <div class="flex justify-between items-center px-5 py-5 border-b border-white">
      <div></div>
      <div class="flex">
        <input class="px-3 py-1 border-2 border-white bg-transparent rounded-md focus:shadow-glow focus:shadow-white text-white outline-none select-none" placeholder="Search"/>
      </div>
    </div>
    <table class="table-auto w-full px-5 text-left border-collapse">
      <thead class="border-b border-white">
        <tr>
          <th class="w-5 pl-3">
            <div class="w-5 h-5 border-2 border-gray-400 rounded-md"></div>
          </th>
          <th
            v-for="header in headers"
            :key="header.key"
            @click="sortBy(header.key)"
            class="px-5 py-3 cursor-pointer"
          >
            {{ header.label }}
            <span v-if="sortKey === header.key">
              {{ sortOrder === 'asc' ? '↑' : '↓' }}
            </span>
          </th>
          <th class="px-5 py-3">
            <span>ACTIONS</span>
          </th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="item in sortedItems"
          :key="item.id"
          class="border-b border-white hover:shadow-glow hover:shadow-white"
        >
          <td class="w-5 pl-3">
            <div class="w-5 h-5 border-2 border-white rounded-md"></div>
          </td>
          <td v-for="header in headers" :key="header.key" class="px-5 py-4">
            {{ item[header.key] }}
          </td>
          <td class="w-5">
            <div class="flex px-5 py-4">
              <div
              @click="console.log(item)"
              class="flex justify-center items-center p-2 mr-1 border-2 border-blue-200 hover:bg-blue-200 rounded-full cursor-pointer group">
                <Icon class="text-blue-300 group-hover:text-blue-500 text-lg" :name="'formkit:list'"></Icon>
              </div>
              <div class="flex justify-center items-center p-2 mr-1 border-2 border-green-200 hover:bg-green-200 rounded-full cursor-pointer group">
                <Icon class="text-green-300 group-hover:text-green-500 text-2xl" :name="'tdesign:edit'"></Icon>
              </div>
              <div class="flex justify-center items-center p-2 mr-1 border-2 border-red-200 hover:bg-red-200 rounded-full cursor-pointer group">
                <Icon class="text-red-300 group-hover:text-red-500 text-2xl" :name="'mynaui:trash'"></Icon>
              </div>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
    <div class="flex justify-between items-center px-5 py-5">
      <div>
        <span>Showing 1 to 7 of 100 entries</span>
      </div>
      <div class="flex justify-center items-center">
        <label class="w-10 h-10 flex justify-center items-center mr-1 bg-transparent border-2 border-gray-200 hover:border-white rounded-full cursor-pointer"><</label>
        <label class="w-10 h-10 flex justify-center items-center mr-1 bg-transparent border-2 border-gray-200 hover:border-white rounded-full cursor-pointer">1</label>
        <label class="w-10 h-10 flex justify-center items-center mr-1 bg-transparent border-2 border-gray-200 hover:border-white rounded-full cursor-pointer">2</label>
        <label class="w-10 h-10 flex justify-center items-center mr-1 bg-transparent border-2 border-gray-200 hover:border-white rounded-full cursor-pointer">3</label>
        <label class="w-10 h-10 flex justify-center items-center mr-1 bg-transparent border-2 border-gray-200 hover:border-white rounded-full cursor-pointer">></label>
      </div>
    </div>
  </div>
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

const sortKey = ref("");
const sortOrder = ref("asc");

const sortBy = (key) => {
  if (sortKey.value === key) {
    sortOrder.value = sortOrder.value === "asc" ? "desc" : "asc";
  } else {
    sortKey.value = key;
    sortOrder.value = "asc";
  }
};

const sortedItems = computed(() => {
  if (!sortKey.value) return items.value;
  return [...items.value].sort((a, b) => {
    const result =
      a[sortKey.value] > b[sortKey.value]
        ? 1
        : a[sortKey.value] < b[sortKey.value]
        ? -1
        : 0;
    return sortOrder.value === "asc" ? result : -result;
  });
});

</script>
  