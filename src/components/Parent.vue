<template>
	<div class="parent">
		<h2>Parent.vue</h2>
		<p>count: {{ count }}</p>

		<div class="parent__button">
			<button type="button" @click="increaseCountOne()">ChildOne 카운트 증가</button>
		</div>

		<div class="parent__button">
			<button type="button" @click="increaseCountTwo()">ChildTwo 카운트 증가</button>
		</div>

		<ChildOne :count="countOne" />
		<ChildTwo :count="countTwo" />
	</div>
</template>

<script setup lang="ts">
	import { ref , onUpdated, onMounted, onUnmounted} from 'vue';
	import ChildOne from './ChildOne.vue';
	import ChildTwo from './ChildTwo.vue';

	defineProps<{
		count: number;
	}>();

	const countOne = ref(0);
	const countTwo = ref(0);

	const increaseCountOne = () => {
		console.log('💡 [Parent] increase ChildOne count');
		countOne.value += 1;
	};

	const increaseCountTwo = () => {
		console.log('💡 [Parent] increase ChildTwo count');
		countTwo.value += 1;
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