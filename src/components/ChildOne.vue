<template>
	<div class="child">
		<h3>ChildOne</h3>
		<p>count: {{ count }}</p>
	 </div>
</template>

<script setup lang="ts">
	import { onUpdated, onUnmounted, onMounted } from 'vue';

	defineProps<{
		count: number;
	}>();

	onMounted(() => {
		console.log(`💡 [ChildOne] mounted`);
	});

	onUpdated(() => {
		console.log(`💡 [ChildOne] DOM updated`);
	});

	onUnmounted(() => {
		console.log(`💡 [ChildOne] unmounted`);
	});
</script>

<style scoped>
	.child {
		margin-top: 10px;
		padding: 10px;
		border: 1px solid #ddd;
	}
</style>