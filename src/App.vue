<script setup>
import { reactive } from "vue";
import { items } from "./movies.json";
import { StarIcon } from "@heroicons/vue/24/solid";

const movies = reactive(items);
</script>

<template>
  <h1 class="flex bg-slate-900 w-screen h-screen justify-center items-center">
    <h2 class="flex flex-row">
      <div v-for="movie in movies" class="w-72 pr-3" :key="movie.id">
        <img :src="movie.image" class="w-72 rounded-tl-md rounded-tr-md h-96" />
        <div
          class="flex flex-col bg-white p-2 h-56 justify-between rounded-bl-md rounded-br-md"
        >
          <div>
            <div class="text-xl">
              {{ movie.name }}
            </div>
            <div class="flex flex-row pt-1 pb-1">
              <div
                v-for="genre in movie.genres"
                class="bg-indigo-500 rounded-lg pr-1 mr-1 pl-1 text-white"
              >
                {{ genre }}
              </div>
            </div>
            <div class="text-sm pt-2">
              {{ movie.description }}
            </div>
          </div>
          <div class="flex flex-row items-center">
            Rating ({{ movie.rating }}/5)
            <div
              v-for="star in movie.rating"
              class="pl-1"
              :key="`star-${star}`"
            >
              <StarIcon class="w-5 h-5 fill-yellow-500" />
            </div>
          </div>
        </div>
      </div>
    </h2>
  </h1>
</template>
