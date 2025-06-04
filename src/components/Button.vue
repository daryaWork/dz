<template>
  <button class="button">
    <slot>Начать игру</slot>
  </button>
</template>

<style scoped>
.button {
  cursor: pointer;
  border: none;
  outline: none;
  background: var(--bg-button);
  font-size: 24px;
  border-radius: 100px;
  padding: 20px 50px;
  color: var(--color-white);
  font-weight: 400;
}
</style>