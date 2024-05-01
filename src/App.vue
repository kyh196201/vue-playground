<script setup>
import { ref, onUpdated } from 'vue';
import Parent from './components/Parent.vue';

const number = ref(0);
const key = ref(0);

onUpdated(() => {
  console.log('💡 [App] updated');
});
</script>

<template>
  <div class="app">
    <h2>App.vue</h2>

    <div class="buttons">
      <button type="button" @click="number += 1">카운트 증가</button>
      <button type="button" @click="key += 1">Parent Key 변경</button>
    </div>

    <Parent :count="number" :key="key" />
  </div>

</template>

<style scoped>
  .app {
    padding: 10px;
		border: 1px solid #ddd
  }

  .buttons button:first-child {
    margin-right: 4px;
  }
</style>
