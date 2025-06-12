<template>
  <Header />
  <main>
    <Card v-for="card in cards" :card="card" :key="card.cardNumber" />
    <!-- <Button /> -->
  </main>
</template>

<script setup lang="ts">
import Button from './components/Button.vue';
import Header from './components/Header.vue';
import Card from './components/Card.vue';

const cards = [
  {
  cardNumber: '09',
  word: 'letter',
  translation: 'слово',
}, {
  cardNumber: '09',
  word: 'letter',
  translation: 'слово',
}
]
</script>

<style scoped>
main {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
</style>

