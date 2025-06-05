<template>
  <div class="card" :class="{ 'is-flipped': isFlipped }" @click="handleClick">
    <div class="card__wrapper">
      <div class="front">
        <span class="card__count">{{ card.cardNumber }}</span>
        <p class="card__word">{{ card.word }}</p>
        <span class="card__action">перевернуть</span>
      </div>
      <div class="back">
        <span class="card__count">{{ card.cardNumber }}</span>
          <p class="card__word">{{ card.translation }}</p>
          <div class="card__button">
            <CloseIcon />
            <ApproveIcon />
          </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';
import ApproveIcon from '../icons/ApproveIcon.vue';
import CloseIcon from '../icons/CloseIcon.vue';

const isFlipped = ref(false);

const props = defineProps({
  card: {
    type: Object,
    required: true
  }
})

const handleClick = () => {
  isFlipped.value = !isFlipped.value;
}
</script>

<style scoped>
.card {
  width: 210px;
  height: 336px;
  border-radius: 16px;
  color: var(--color-black);
  font-size: 18px;
  cursor: pointer;
  position: relative;
  perspective: 1000px;
}

.card__wrapper {
  border: 1px solid var(--color-light-blue);
  border-radius: 16px;
  height: 100%;
  width: 100%;
  position: relative;
  transform-style: preserve-3d;
  transition: transform .6s linear;
  padding: 20px;
  background-color: var(--color-white);
}

.card__count {
  position: absolute;
  left: 5px;
  top: -10px;
  padding: 0 5px;
  background-color: var(--color-white);
}

.card__word {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  margin: 0;
}

.card__action {
  position: absolute;
  bottom: -13px;
  left: 50%;
  transform: translateX(-50%);
  padding: 0 10px;
  background-color: var(--color-white);
}

.card__button {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  background-color: var(--color-white);
  bottom: -20px;
  padding: 0 10px;
}

.front,
.back {
  backface-visibility: hidden;
  position: absolute;
  border: 1px solid var(--color-light-blue);
  top: 20px;
  left: 20px;
  bottom: 20px;
  right: 20px;
  border-radius: 18px;
}

.back {
  transform: rotateY(180deg);
}

.card.is-flipped .card__wrapper {
  transform: rotateY(180deg);
}
</style>