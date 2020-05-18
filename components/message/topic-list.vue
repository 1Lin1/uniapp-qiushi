<template>
	<view class="topic-list">
		<!-- 搜索框 -->
		<view class="search-input">
			<input type="text" :cursor="500" placeholder-class="icon iconfont icon-sousuo u-f-ajc" placeholder="搜索内容"/>
		</view>
		<!-- 轮播图 -->
		<swiper class="topic-swiper":indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
			<block v-for="(item,index) in swiperData" :key="index">
				<swiper-item class="swiper-item">
					<image :src="item.src"  lazy-load></image>
				</swiper-item>
			</block>
			
		</swiper>
		<!-- 热门分类 -->
		<topic-category></topic-category>
		
		<!-- 最近更新 -->
		<topic-new :topicNewList="topicNewList"></topic-new>
		
		
	</view>
</template>

<script>
	import topicCategory from './topic-category.vue'
	import topicNew from './topic-new.vue'
	export default{
		components:{
			topicCategory,
			topicNew
		},
		props:{
			topicNewList:Array,
		},
		data(){
			return{
				swiperData:[
					{src:'../../static/image/banner2.jpg'},
					{src:'../../static/image/banner2.jpg'},
					{src:'../../static/image/banner2.jpg'},
				],
				
					
			}
		}
	}
</script>

<style lang="scss" scoped>
	$topic-common-font-size:40rpx;
	
	
	// 输入框
	.search-input{
		padding: 20rpx 28rpx 10rpx 20rpx ;
		input{
			padding:0 8rpx;
			line-height: 70rpx;
			height: 70rpx;
			width: 100%;
			background-color: #F4F4F4;
		}
	}
	
	// 轮播图
	.topic-swiper{
		padding: 0 20rpx 20rpx;
		border-radius: 1rpx solid #F4F4F4;
		.swiper-item{
				text-align: center;
				image{
					width: 100%;
					height: 100%;
					border-radius: 15rpx;
				}
		}
	}
	
	
</style>
