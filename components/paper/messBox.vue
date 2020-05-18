<template>
	<view class="mess-box">
		<block v-for="(item,index) in messList" :key="index">
			<mess-item :messItem="item"></mess-item>
		</block>
	</view>
</template>

<script>
	import messItem from './messItem.vue';
	export default {
		components: {
			messItem
		},
		props: {
			messList: Array
		}
	}
</script>

<style>
</style>
