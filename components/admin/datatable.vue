<template>
    <div class="bg-[#1e1d22] rounded-lg shadow-glow shadow-white">
      <div class="flex justify-between items-center px-5 py-5 border-b border-white">
        <!-- Title -->
        <label class="text-2xl text-bold">{{ tableName }}</label>
        <!-- Buttons -->
        <div class="flex gap-1">
          <div class="flex items-center px-3 py-1 border-2 border-blue-400 hover:border-transparent hover:bg-blue-200 rounded-md cursor-pointer group">
            <Icon class="text-base text-blue-200 group-hover:text-blue-500" :name="'fluent-emoji-high-contrast:plus'"></Icon>
            <span class="ml-2 text-blue-200 group-hover:text-blue-500">New Data</span>
          </div>
          <div class="flex items-center px-3 py-1 border-2 border-red-400 hover:border-transparent hover:bg-red-200 rounded-md cursor-pointer group">
            <Icon class="text-lg text-red-200 group-hover:text-red-500" :name="'mynaui:trash'"></Icon>
            <span class="ml-2 text-red-200 group-hover:text-red-500">Batch Delete Data</span>
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
              :class="header.headerClass"
              class="px-5 py-3 cursor-pointer"
            >
              {{ header.label }}
              <span v-if="sortKey === header.key">
                {{ sortOrder === 'asc' ? '↑' : '↓' }}
              </span>
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
            <td v-for="header in headers" :key="header.key" class="px-5 py-4" :class="header.itemClass">
              <slot
                :name="`${header.key}`"
                :item="item"
              >
                {{ item[header.key] }} <!-- 預設回退內容 -->
              </slot>
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
  import { defineProps, computed } from "vue";

  const props = defineProps({
    tableName: String,
    headers: Array,
    items: Array,
  });

  const headers = ref(props.headers);
  const items = ref(props.items);
    
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
    