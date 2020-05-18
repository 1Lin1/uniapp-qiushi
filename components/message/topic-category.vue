<template>
	<view class="topic-category">
		<view class="top u-f-jb">
			<view class="left">
				热门分类
			</view>
			<view class="right u-f"  @click="toMoreCate">
				<text>更多</text>
				<view class="icon iconfont icon-jinru">
				</view>
			</view>
		</view>
		
		<view class="bottom u-f-aje">
			<block v-for="(item,index) in cateList" :key="index">
				<view class="bottom-item">{{item.name}}</view>
			</block>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return {
				cateList:[
					{name:'最新'},
					{name:'游戏'},
					{name:'情感'},
					{name:'打卡'},
					{name:'故事'},
					{name:'喜爱'},
				]
			}
		},
		methods:{
			toMoreCate(){
				uni.navigateTo({
				    url:'../../pages/topic-moreCate/topic-moreCate'
				});
			}
		}
	}
</script>

<style lang="scss" scoped>
	// 热门分类
	.topic-category{
		
		padding: 20rpx;
		height: 200rpx;
		border-top: 1rpx solid #f4f4f4;
		border-bottom: 1rpx solid #F4F4F4;
		.top{
			.left,.right{
				font-size:$my-font-size-lg;
				font-weight:  500;
			}
			.right{
				color: #dbdbdb;
				.icon{
					font-size: $my-font-size-lg;
				}
			}
		}
		.bottom{
			margin-top: 20rpx;
			.bottom-item{
				color:#aaaaaa;
				padding: 6rpx 16rpx 6rpx;
				font-size:$my-font-size-base;
				font-weight:  530;
				background-color: #f9f9f9;
				margin-right:10rpx;
			}
		}
	}
</style>
