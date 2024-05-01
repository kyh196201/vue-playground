<template>
  <div class="app">
    <h2>App.vue</h2>

    <div class="buttons">
      <button type="button" @click="increase()">Parent 카운트 증가</button>
      <button type="button" @click="key += 1">Parent Key 변경</button>
    </div>

    <Parent :count="count" :key="key" />
  </div>

</template>

<script setup>
  import { ref, onUpdated, onMounted } from 'vue';
  import Parent from './components/Parent.vue';

  const count = ref(0);
  const key = ref(0);

  const increase = () => {
    console.log('💡 [App] increase Parent count');
    count.value += 1;
  };

  onMounted(() => {
    console.log('💡 [App] mounted');
  });

  onUpdated(() => {
    console.log('💡 [App] DOM updated');
  });
</script>

<style scoped>
  .app {
    padding: 10px;
		border: 1px solid #ddd
  }

  .buttons button:first-child {
    margin-right: 4px;
  }
</style>
