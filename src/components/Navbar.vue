<template>
    <header class="bg-white shadow h-16 flex justify-between items-stretch">
        <div class="flex items-center">
            <router-link :to="{ name: 'home' }"
                class="text-center inline-flex items-center h-full px-4 text-orange-500 font-bold hover:bg-orange-500 hover:text-white ml-2 sm:ml-8"
                @click="show = false">
                Home
            </router-link>
            <router-link to="/"
                class="text-center inline-flex items-center h-full px-4 text-orange-500 font-bold hover:bg-orange-500 hover:text-white"
                @click="show = false">
                My Recipes
            </router-link>
        </div>
        <div class="relative">
            <button class="font-semibold px-2 h-full transition-colors hover:bg-orange-500 hover:text-white mr-2 sm:mr-8"
                @click="show = !show">
                Search Recipes
            </button>
            <div v-if="show" class="absolute right-0 mr-8">
                <router-link :to="{ name: 'byName' }"
                    class="inline-flex items-center font-semibold px-4 h-full bg-white border-2 rounded transition-colors hover:bg-orange-500 hover:text-white hover:border-orange-500 block w-full"
                    @click="show = false">
                    By Name
                </router-link>
                <router-link :to="{ name: 'byLetter' }"
                    class="inline-flex items-center font-semibold px-4 h-full bg-white border-2 rounded transition-colors hover:bg-orange-500 hover:text-white hover:border-orange-500 block w-full"
                    @click="show = false">
                    By Letter
                </router-link>
                <router-link :to="{ name: 'ingredients' }"
                    class="inline-flex items-center font-semibold px-4 h-full bg-white border-2 rounded transition-colors hover:bg-orange-500 hover:text-white hover:border-orange-500 block w-full"
                    @click="show = false">
                    By Ingredients
                </router-link>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    data() {
        return {
            show: false
        }
    }
}
</script>