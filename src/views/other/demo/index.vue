<template>
	<div>
		<el-input v-model="count"></el-input>
		<div>{{ plusOne }}</div>
	</div>
</template>

<script setup lang="ts">
import { computed, ref } from "vue";
const count = ref<number>(0);
const plusOne = computed(() => count.value + 1, {
	// 初始化渲染的时候
	// onTrack(e) {
	// 	debugger;
	// 	console.log("onTrack", e);
	// },
	// 当内容发生百变的时候
	// onTrigger(e) {
	// 	debugger;
	// 	console.log("onTrigger", e);
	// }
});
</script>

<style scoped></style>
