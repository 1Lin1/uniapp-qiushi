<template>
	<view class="topic-new">
		<!-- 标题 -->
		<view class="new-title">
			最近更新
		</view>
		
		<block v-for="(item,index) in topicNewList" :key="index">
			<view class="topic-newContent u-f-ac"  @tap="toTopicDetail(item.id)">
				<view class="new-img">
					<image :src="item.src" mode="scaleToFill" lazy-load></image>
				</view>
				
				<view class="new-left-content">
					<view>#{{item.title}}#</view>
					<view>{{item.desc}}</view>
					<view>动态{{item.totalNum}} 今日{{item.todayNum}}</view>
				</view>
			</view>
		</block>
		
	</view>
</template>

<script>
	export default{
		props:{
			topicNewList:Array
		},
		methods:{
			toTopicDetail(id){
				uni.navigateTo({
					url: '../../pages/topic-detail/topic-detail?id=' + id,
				});
			}
		}
	}
</script>

<style lang="scss" scoped>
	// 最近更新
	.topic-new{
		padding: $common-padding;
		.new-title{
			font-size: $my-font-size-lg;
		}
		.topic-newContent{
			margin-top: 40rpx;
			border-bottom: 1rpx solid #F4F4F4;
			.new-img{
				flex-shrink: 0;
				image{
					width: 160rpx;
					height: 160rpx;
					border-radius: 20rpx;
				}
			}
			
			.new-left-content{
				padding: 0 40rpx 20rpx;
				view{
					&:nth-child(1){
						font-size: $my-font-size-lg;
					}
					
					&:nth-child(2){
						font-size: $my-font-size-sm;
						color:$uni-text-color-disable;
					}
					
					&:nth-child(3){
						font-size: $my-font-size-sm;
						color:$uni-text-color-disable;
					}
				}
				
			}
		}
	}
</style>
