<script setup lang="ts">
/* Imports */
import { computed } from 'vue';
import type { Dish } from '../views/types';

type PropTypes = {
  dish: Dish;
};

/* Props */
const props = defineProps<PropTypes>();

/* Emits */
const emits = defineEmits<{
  (event: 'delete-dish', dish: Dish): void;
}>();

/* Computed */
const statusColor = computed(() => {
  const statusColorMap = {
    'Want to Try': 'is-warning',
    Recommended: 'is-success',
    'Do Not Recommend': 'is-danger',
  };

  return statusColorMap[props.dish.status] || '';
});

/* Methods */
const deleteDish = () => {
  emits('delete-dish', props.dish);
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
          {{ props.dish.name }}
        </p>
        <p class="subtitle mb-2">
          <span class="tag" :class="statusColor">{{ props.dish.status }}</span>
        </p>
        <div>
          <button @click="deleteDish" class="button is-small is-danger is-light">Delete</button>
        </div>
      </div>
    </div>
  </article>
</template>

<style></style>
