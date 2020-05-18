<template>
	<view>
		<!-- 导航栏 -->
		<tab-bar :tabBars="tabBars" :tabIndex="tabIndex"></tab-bar>
		
	</view>
</template>

<script>
	import tabBar from '../../components/common/tabBar.vue';
	
	export default {
		components:{
			tabBar
		},
		data() {
			return {
				tabIndex:0,
				tabBars:[
					{
						name:'糗友',
						id:'qiuyou'
					},
					{
						name:'动态',
						id:'dongtai'
					}
				]
			};
		},
		onNavigationBarButtonTap(e){
			if(e.index === 0){
				uni.switchTab({
					url:'../paper/paper'
				})
			}
		},
		
		//监听输入
		onNavigationBarSearchInputChanged(e){
			console.log(e.text)
			
		}
	}
</script>

<style lang="scss" scoped>
	

</style>
