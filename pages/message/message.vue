<template>
	<view>
	
	
	<!-- 轮播图视图 -->
		<message-swiper :swiperHeight="swiperHeight"></message-swiper>
	</view>
</template>

<script>
	import messageSwiper from '../../components/message/message-swiper.vue'
	export default {
		components:{
			messageSwiper
		},
		data() {
			return {
				
				swiperHeight:0,
			}
		},
		// 动态获取手机屏幕高度
		onLoad() {
			uni.getSystemInfo({
			    success: (res) => {
					// 动态获取手机屏幕高度
			        this.swiperHeight = res.windowHeight;
					console.log(this.swiperHeight)
			      
			    }
			});
		},
	}
</script>

<style >
	
	
	

</style>
