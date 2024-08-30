<script setup lang="ts">
/* Imports */
import { computed } from 'vue';
import type { Restaurant } from '../views/types';

type PropTypes = {
  restaurant: Restaurant;
};

/* Props */
const props = defineProps<PropTypes>();

/* Emits */
const emits = defineEmits<{
  (event: 'delete-restaurant', restaurant: Restaurant): void;
}>();

/* Computed */
const statusColor = computed(() => {
  const statusColorMap = {
    'Want to Try': 'is-warning',
    Recommended: 'is-success',
    'Do Not Recommend': 'is-danger',
  };

  return statusColorMap[props.restaurant.status] || '';
});

/* Methods */
const deleteRestaurant = () => {
  emits('delete-restaurant', props.restaurant);
};
</script>

<template>
  <article class="box">
    <div class="media">
      <aside class="media-left">
        <img src="https://placehold.jp/150x150.png" alt="" />
      </aside>
      <div class="media-content">
        <p class="title is-4 is-spaced mb-1">
          {{ restaurant.name }}
        </p>
        <p class="subtitle mb-2">
          <span class="tag" :class="statusColor">{{ restaurant.status }}</span>
        </p>
        <div class="content mb-2">
          {{ restaurant.address }}
        </div>
        <div>
          <button @click="deleteRestaurant" class="button is-small is-danger is-light">Delete</button>
        </div>
      </div>
    </div>
  </article>
</template>

<style></style>
