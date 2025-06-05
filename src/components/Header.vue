<template>
  <header class="header">
    <p class="header__title">Запомни слово</p>

    <Score :score="score" />
  </header>
</template>

<script setup lang="ts">
import Score from './Score.vue';
const score = 100;
</script>

<style>
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 16px;
}

.header__title {
  color: var(--color-grey);
  text-transform: uppercase;
  font-weight: 600;
}
</style>