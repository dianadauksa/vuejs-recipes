<template>
    <div class="max-w-[1200px] mx-auto p-8 grid grid-cols-1 md:grid-cols-3">
        <div class="mx-4">
            <h1 class="text-4xl font-bold mb-2 mt-2 text-orange-500 text-center">{{ meal.strMeal }}</h1>
            <img :src="meal.strMealThumb" :alt="meal.strMeal" class="w-full rounded">
            <div class="grid grid-cols-1 sm:grid-cols-2 text-lg py-2 text-center">
                <div>
                    <strong class="font-semibold">Category:</strong> {{ meal.strCategory }}
                </div>
                <div>
                    <strong class="font-semibold">Area:</strong> {{ meal.strArea }}
                </div>
            </div>
            <div v-if="meal.strTags" class="text-center mb-6">
                <strong class="font-semibold">Tags:</strong> {{ meal.strTags }}
            </div>
            <div class="grid grid-cols-1 sm:grid-cols-2 py-2 text-lg text-center">
                <div class="mb-4">
                    <YouTubeButton :href="meal.strYoutube" />
                </div>
                <div>
                    <a :href="meal.strSource" target="_blank"
                        class="px-3 py-2 rounded border-2 text-white border-blue-500 bg-blue-500 hover:bg-blue-600 transition-colors">
                        Original
                    </a>
                </div>

            </div>
        </div>
        <div class="mx-4">
            <h1 class="text-3xl font-bold mt-2 mb-2">Ingredients</h1>
            <ul>
                <template v-for="(el, ind) of new Array(20)">
                    <li v-if="meal[`strIngredient${ind + 1}`]">
                        {{ ind + 1 }}. {{ meal[`strIngredient${ind + 1}`] }} - {{ meal[`strMeasure${ind + 1}`] }}
                    </li>
                </template>
            </ul>
        </div>
        <div class="mx-4">
            <h1 class="text-3xl font-bold mt-2 mb-2">Instructions</h1>
            <div class="text-justify">
                {{ meal.strInstructions }}
            </div>
        </div>
    </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import { useRoute } from 'vue-router';
import axiosClient from '../axiosClient';
import YouTubeButton from '../components/YouTubeButton.vue';
const route = useRoute();
const meal = ref({})
onMounted(() => {
    axiosClient.get(`lookup.php?i=${route.params.id}`)
        .then(({ data }) => {
            meal.value = data.meals[0] || {}
        })
})
</script>