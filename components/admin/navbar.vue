<template>
    <div class="flex justify-between items-center mx-8 mt-5 px-5  bg-[#1e1d22] rounded-md">
        <div class="flex py-5">
            <label class="text-lg">Dashboard</label>
            <span class="mx-3">|</span>
            <div>
                <label class="text-base">home</label>
                <span class="mx-2">></span>
                <label class="text-base">Dashboard</label>
            </div>
        </div>
        <!-- Right -->
        <div class="flex py-2">
            <!-- Profile -->
            <div class="relative group">
                <div class="w-14 h-14 rounded-full">
                    <img class="border-2 border-transparent group-hover:border-white rounded-full group-hover:shadow-glow group-hover:shadow-white cursor-pointer" src="/assets/images/lynn_1.png"/>
                </div>
                <div class="hidden group-hover:block absolute -left-5 bg-white text-[#555] rounded-md transition duration-300 ease-in-out">
                    <ul class="p-3">
                        <li class="py-1">Profile</li>
                        <li class="py-1">Setting</li>
                        <hr>
                        <li
                        @click="console.log('log out now!')"
                        class="pt-1 cursor-pointer">Logout</li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>
<script setup>
import { ref } from 'vue';

const isProfileOpen = ref(false);
</script>