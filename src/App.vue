<script setup>
/* Imports */
import { ref } from 'vue';

/* Components */
import TheNavbar from './components/TheNavbar.vue';
import TheFooter from './components/TheFooter.vue';

/* State */
const state = ref({
  tagline: 'The updated tagline',
});
</script>

<template>
  <TheNavbar :tagline="state.tagline" />
  <RouterView />
  <TheFooter />
</template>

<style></style>
