<template>
  <div class="card" :class="{ 'is-flipped': isFlipped }" @click="handleClick">
    <div class="card__wrapper">
      <div class="front">
        <span class="card__count">{{ card.cardNumber }}</span>
        <p class="card__word">{{ card.word }}</p>
        <span v-if="!showButtons" class="card__action">перевернуть</span>
        <div v-else class="card__button">
            <CloseIcon @click.stop="handleReject" />
            <ApproveIcon @click.stop="handleApprove" />
        </div>
      </div>
      <div class="back">
        <ApproveIcon v-if="status === 'success'" class="big-icon " />
        <CloseIcon v-else-if="status === 'failed'" class="big-icon" />
        <span class="card__count">{{ card.cardNumber }}</span>
          <p class="card__word">{{ card.translation }}</p>

      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';
import ApproveIcon from '../icons/ApproveIcon.vue';
import CloseIcon from '../icons/CloseIcon.vue';

type Status = 'pending' | 'success' | 'failed';

const isFlipped = ref(false);
const showButtons = ref(true);
const status = ref<Status>('pending');

const props = defineProps({
  card: {
    type: Object,
    required: true
  }
})

const handleClick = () => {
  isFlipped.value = !isFlipped.value;
}

const handleApprove = () => {
  status.value = 'success';
}

const handleReject = () => {
  status.value = 'failed';
}
</script>

<style scoped>
.card {
  width: 240px;
  height: 376px;
  border-radius: 16px;
  color: var(--color-black);
  font-size: 18px;
  cursor: pointer;
  position: relative;
  perspective: 1000px;
  padding: 20px;
}

.card__wrapper {
  border: 1px solid var(--color-light-blue);
  border-radius: 16px;
  height: 100%;
  width: 100%;
  position: relative;
  transform-style: preserve-3d;
  transition: transform .6s linear;
  /* padding: 20px; */
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
  bottom: -14px;
  padding: 0 10px;
  display: flex;
  gap: 10px;
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

.front {
  opacity: 1;
}

.card.is-flipped .front {
  opacity: 0;
}

.big-icon {
  width: 42px;
  height: 42px;
  left: 50%;
  transform: translateX(-50%);
  position: absolute;
  top: -20px;
  z-index: 1;
}
</style>