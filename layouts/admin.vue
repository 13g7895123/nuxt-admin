<template>
  <div class="admin-layout h-screen relative flex">
    <!-- mask -->
    <div v-if="isMaskOpen === true" class="absolute top-0 left-0 w-full h-full bg-red-100 opacity-50"></div>
    <AdminSidebar/>  
    <div class="flex-1 flex flex-col bg-[#151419] text-white">
      <AdminNavbar/>
      <!-- Main Content -->
      <main class="flex-1 mx-8 px-1 pb-2 pt-5 overflow-y-auto scrollbar">
        <slot></slot>
      </main>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const isMaskOpen = ref(false);
</script>

<style scoped>
.admin-layout {
  font-family: Arial, sans-serif;
}
.scrollbar{
  &::-webkit-scrollbar{
    width: 10px;
    height: 1px;
  }
  &::-webkit-scrollbar-track {
    border: 1px solid #fff;
    background-color: #000;
    border-radius: 10px;
    margin: 260px 130px;
  }
  &::-webkit-scrollbar-thumb{
    border-radius: 10px;
    background-color: rgb(201, 201, 201);
  }
}
</style>
  