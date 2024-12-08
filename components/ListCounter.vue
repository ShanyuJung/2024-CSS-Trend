<script setup lang="ts">
import { ref, watch } from "vue";

const props = defineProps({
  count: {
    type: Number,
    default: 0,
  },
});

const counter = ref(props.count);
watch(
  () => props.count,
  (newCount) => {
    counter.value = newCount;
  }
);
</script>

<template>
  <div class="listCounter">
    <ul flex="~">
      <li v-for="item in counter" :key="item">item {{ item }}</li>
    </ul>
    <div flex="~" w="min" border="~ main rounded-md">
      <button
        border="r main"
        p="2"
        font="mono"
        outline="!none"
        hover:bg="gray-400 opacity-20"
        @click="counter -= 1"
      >
        -
      </button>
      <span m="auto" p="2">{{ counter }}</span>
      <button
        border="l main"
        p="2"
        font="mono"
        outline="!none"
        hover:bg="gray-400 opacity-20"
        @click="counter += 1"
      >
        +
      </button>
    </div>
  </div>
</template>

<style>
.listCounter {
  ul:has(> :nth-child(5)) {
    outline: 1px solid green;
  }

  ul:has(> :nth-child(5):last-child) {
    outline: 1px solid blue;
  }

  ul:not(:has(> :nth-child(5))) {
    outline: 1px solid red;
  }
}
</style>
