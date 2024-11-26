<template>
    <div class="admin-layout h-screen flex">
      <AdminSidebar/>  
      <div class="flex-1 flex flex-col bg-[#151419] text-white">
        <AdminNavbar/>
        <!-- Main Content -->
        <main class="flex-1 mx-8 px-1 pb-2 pt-5 overflow-y-auto">
          <slot></slot>
        </main>
      </div>
    </div>
  </template>
  
  <script setup>
  </script>
  
  <style scoped>
  .admin-layout {
    font-family: Arial, sans-serif;
  }
  </style>
  