<template>
  <div>
    <div class="p-8 pb-0">
      <h1 class="text-4xl font-bold mb-4 text-[#1DB954]">Search Meals by Name</h1>
    </div>
    <div class="px-8 pb-3">
      <input
        type="text"
        v-model="keyword"
        class="rounded border-2 bg-white border-gray-200 focus:ring-[#1DB954] focus:border-[#1DB954] w-full"
        placeholder="Search for Meals"
        @change="searchMeals"
      />
    </div>

    <Meals :meals="meals" />
  </div>
</template>

<script setup>
import { computed, onMounted, ref } from "vue";
import store from "../store";
import { useRoute } from "vue-router";
import YouTubeButton from "../components/YouTubeButton.vue";
import MealItem from "../components/MealItem.vue";
import Meals from "../components/Meals.vue";

const router = useRoute();

const keyword = ref("");

const meals = computed(() => store.state.searchedMeals);

function searchMeals() {
  if (keyword.value) {
    store.dispatch("searchMeals", keyword.value);
  } else {
    store.commit("setSearchedMeals", []);
  }
}

onMounted(() => {
  keyword.value = router.params.name;
  if (keyword.value) {
    searchMeals();
  }
});
</script>
