<script setup>
import { ref } from 'vue'

const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  description: {
    type: String,
    required: true,
  },
  imgPath: {
    type: String,
    required: true,
  },
  isLastItem: {
    type: Boolean,
    required: false,
    default: false,
  },
})

let imgSrc = ref()

import(props.imgPath).then((img) => {
  imgSrc.value = img.default
})
</script>

<template>
  <div class="work-item">
    <div class="test">
      <div class="work-icon-border">
        <img v-if="imgSrc" class="work-icon" :src="imgSrc" />
      </div>
      <div :class="{ wall: !isLastItem }"></div>
    </div>
    <div class="item-info">
      <h2>
        <a href="https://www.bamtech.net" target="_blank">{{ title }}</a>
      </h2>
      <p>{{ description }}</p>
    </div>
  </div>
</template>

<style scoped>
.work-icon-border {
  height: 54px;
  width: 54px;
  border: 2px var(--vt-c-indigo) solid;
  border-radius: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.test {
  display: flex;
  flex-direction: column;
}

.wall {
  margin-left: 27px;
  border-left: 2px var(--vt-c-indigo) solid;
  height: calc(100% - 54px);
}

.work-item {
  display: flex;
  gap: 0.5rem;
}
.work-icon {
  height: 35px;
  width: 35px;
}
.item-info {
  display: flex;
  flex-direction: column;
  margin-bottom: 1rem;
}
</style>
