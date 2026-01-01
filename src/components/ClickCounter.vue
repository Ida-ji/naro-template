<script setup lang="ts">
import { ref, computed } from 'vue'

const count = ref<number>(0)
const countMessage = computed(() => '回数: ' + count.value)
</script>

<template>
  <div>
    <div>{{ countMessage }}</div>

    <button @click="count += 1">クリック+1</button>
    <button @click="count += 5">クリック+5</button>
    <button @click="count += 10">クリック+10</button>

    <button @click="count = 0">リセット！</button>
  </div>
</template>

<style>
button {
  margin-right: 8px;
}
</style>
