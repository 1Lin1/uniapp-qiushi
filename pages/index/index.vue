<template>
	<view>
		<!-- 顶部导航栏 -->
		<swiper-list  :swiperHeight="swiperHeight"></swiper-list>
		
		
		
	</view>
</template>

<script>
	import swiperList from '../../components/index/swiperList.vue'
	export default {
		data() {
			return {
				swiperHeight:0,
			
			}
		},
		onLoad() {
			uni.getSystemInfo({
			    success: (res) => {
					// 动态获取手机屏幕高度
			        this.swiperHeight = res.windowHeight;
			      
			    }
			});
		},
		components:{
			swiperList
		},
		methods: {
			clickTap(){
				console.log('触发')
			},
		},
		
		//监听输入框点击事件
		onNavigationBarSearchInputClicked() {
			uni.navigateTo({
			    url: '/pages/search/search'
			});
		},
		
		// 监听导航栏按钮事件
		onNavigationBarButtonTap(e) {
			if(e.index === 1){
				uni.navigateTo({
					url:'../add-input/add-input'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	
</style>
