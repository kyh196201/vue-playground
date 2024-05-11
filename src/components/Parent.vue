<template>
	<div class="parent">
		<h2>Parent.vue</h2>
		<p>count: {{ count }}</p>

		<div class="parent__button">
			<button type="button" @click="childCount += 1">Child 카운트 증가</button>
		</div>

		<Child :count="childCount" />
	</div>
</template>

<script setup lang="ts">
	import { ref , onUpdated, onMounted, onUnmounted, reactive} from 'vue';
	import Child from './Child.vue';

	defineProps<{
		count: number;
	}>();

	const childCount = ref(0);

	const increaseCount = () => {
		console.log('💡 [Parent] increase child count');
		childCount.value += 1;
	};

	onMounted(() => {
		console.log('💡 [Parent] mounted');
	});

	onUpdated(() => {
		console.log('💡 [Parent] DOM updated');
	});

	onUnmounted(() => {
		console.log('💡 [Parent] unmounted');
	});
</script>

<style scoped>
	.parent {
		margin-top: 10px;
		padding: 10px;
		border: 1px solid #ddd;
	}
	
	.parent__button + .parent__button {
		margin-top: 10px;
	}
</style>