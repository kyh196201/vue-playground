<template>
	<div class="child">
		<h3>{{ name }}</h3>
	 	<p>count is {{ id }}</p>
	 </div>
</template>

<script setup lang="ts">
	import { onUpdated, onUnmounted, onMounted } from 'vue';

	const props = defineProps<{
		id: number;
		name: string;
	}>();

	onMounted(() => {
		console.log(`💡 [child] ${props.name} mounted`, props.id);
	});

	onUpdated(() => {
		console.log(`💡 [child] ${props.name} updated`, props.id);
	});

	onUnmounted(() => {
		console.log(`💡 [child] ${props.name} unmounted`, props.id);
	});
</script>

<style scoped>
	.child {
		margin-top: 10px;
		padding: 10px;
		border: 1px solid #ddd;
	}
</style>