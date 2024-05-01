<template>
	<div class="parent">
		<h2>Parent.vue</h2>
		<h3>count is {{ count }}</h3>

		<button type="button" @click="count += 1">카운트 증가</button>

		<Child :id="count" name="child1" />
		<Child :id="0" name="child2" />
	</div>
</template>

<script setup lang="ts">
	import { ref , onUpdated, onMounted, onUnmounted} from 'vue';
	import Child from './Child.vue';

	const props = defineProps<{
		count: number;
	}>();

	const count = ref(0);

	onMounted(() => {
		console.log('💡 [parent] mounted');
	});

	onUpdated(() => {
		console.log('💡 [parent] updated', props.count);
	});

	onUnmounted(() => {
		console.log('💡 [parent] unmounted');
	});
</script>

<style scoped>
	.parent {
		margin-top: 10px;
		padding: 10px;
		border: 1px solid #ddd;
	}
</style>