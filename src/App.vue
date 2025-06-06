<template>
  <Header :score="score" />
  <main>
    <Card :card="card" />
    <Button />
  </main>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import Button from './components/Button.vue';
import Header from './components/Header.vue';
import Card from './components/Card.vue';

const score = ref(0);
// status - success | fail | pending
// state - opened | closed

const card = ref({
  cardNumber: '09',
  word: 'letter',
  translation: 'слово',
  state: 'closed',
  status: 'pending'
})
</script>

<style scoped>
main {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
</style>

