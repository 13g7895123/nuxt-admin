<template>
    <div class="admin-layout h-screen flex">
      <AdminSidebar/>  
      <div class="flex-1 flex flex-col bg-[#151419] text-white">
        <AdminNavbar/>
        <!-- Main Content -->
        <main class="flex-1 p-3 pt-5">
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
  