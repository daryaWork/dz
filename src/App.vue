<template>
  <Header />
  <main>
    <Card :card="card" />
    <Button />
  </main>
</template>

<script setup lang="ts">
import Button from './components/Button.vue';
import Header from './components/Header.vue';
import Card from './components/Card.vue';

const card = {
  cardNumber: '09',
  word: 'letter',
  translation: 'слово',
}
</script>

<style scoped>
main {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
</style>

