<template>
	<view>
		<topic-swiper :swiperHeight="swiperHeight"></topic-swiper>
	</view>
</template>

<script>
	import topicSwiper from '../../components/topicMoreCate/topic-Swiper.vue'
	export default {
		components:{
			topicSwiper
		},
		data() {
			return {
				swiperHeight:0,
			};
		},
		
		// 获取高度
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

<style lang="scss">

</style>
