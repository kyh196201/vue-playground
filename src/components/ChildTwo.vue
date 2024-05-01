<template>
	<div class="child">
		<h3>ChildTwo</h3>
		<p>count: {{ count }}</p>
	 </div>
</template>

<script setup lang="ts">
	import { onUpdated, onUnmounted, onMounted } from 'vue';

	defineProps<{
		count: number;
	}>();

	onMounted(() => {
		console.log(`💡 [ChildTwo] mounted`);
	});

	onUpdated(() => {
		console.log(`💡 [ChildTwo] DOM updated`);
	});

	onUnmounted(() => {
		console.log(`💡 [ChildTwo] unmounted`);
	});
</script>

<style scoped>
	.child {
		margin-top: 10px;
		padding: 10px;
		border: 1px solid #ddd;
	}
</style>