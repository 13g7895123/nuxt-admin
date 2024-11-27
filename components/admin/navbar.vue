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
                <!-- Dropdown -->
                <div class="hidden group-hover:block absolute -left-16 bg-white text-[#555] rounded-md transition duration-300 ease-in-out">
                    <ul class="p-3">
                        <li class="flex items-center py-1 cursor-pointer">
                            <Icon class="w-10 text-lg" :name="'icon-park-solid:people'"/>
                            <span>Profile</span>
                        </li>
                        <li class="flex items-center py-1 cursor-pointer">
                            <Icon class="w-10 text-lg" :name="'ic:sharp-settings'"/>
                            <span>Setting</span>
                        </li>
                        <hr>
                        <li
                        @click="console.log('log out now!')"
                        class="flex justify-center items-center mt-1 px-2 py-1 bg-red-400 hover:bg-red-500 text-white rounded-md cursor-pointer">
                            <span>Logout</span>
                            <Icon class="w-5 ml-2 text-lg" :name="'line-md:logout'"/>
                        </li>
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