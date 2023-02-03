<template>
    <navbar />
    <main>
        <div class="max-w-[1200px] mx-auto">
            <router-view />
        </div>
    </main> 
    <footer>
        <div class="bg-white mt-8 shadow h-12 flex justify-between items-stretch">
            
        </div>
    </footer>
</template>

<script setup>
import Navbar from "../components/Navbar.vue";
</script>