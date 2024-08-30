<script setup lang="ts">
/* Imports */
import { ref } from 'vue';

/* Props */
const props = defineProps < {
  tagline: string | number;
  default: 'The best place to find your favorite dish';
} > ();

/* State */ 
const state = ref({
  navList: [
    {
      name: 'Home',
      path: '/',
    },
    {
      name: 'Restaurants',
      path: '/restaurants',
    },
    {
      name: 'Dishes',
      path: '/dishes',
    },
  ],
});
</script>

<template>
  <nav class="navbar has-shadow">
    <div class="navbar-brand">
      <RouterLink to="/" class="navbar-item">
        <img src="@/assets/to-eat-logo.svg" alt="" width="100" />
      </RouterLink>
    </div>
    <div class="navbar-menu">
      <div class="navbar-start">
        <div class="navbar-item">
          <small>{{ props.tagline }}</small>
        </div>
      </div>
      <div class="navbar-end">
        <div v-for="navItem in state.navList" class="navbar-item" :key="`nav-${navItem.name}`">
          <RouterLink :to="navItem.path">{{ navItem.name }}</RouterLink>
        </div>
      </div>
    </div>
  </nav>
</template>

<style></style>
