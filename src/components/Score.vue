<template>
  <span class="score">
    {{score}}
    <HeartIcon />
  </span>
</template>

<script setup lang="ts">
import HeartIcon from '../icons/HeartIcon.vue';

const props = defineProps<{ score: number }>();
</script>

<style scoped>
.score {
  background: var(--color-light-blue);
  color: var(--bg-button);
  border-radius: 36px;
  padding: 10px 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 9px;
}
</style>