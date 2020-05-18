<template>
	<view class="content">
		<view class="detail-bg">
			<image :src="itemInfo.bg" lazy-load></image>
		</view>
		
		<view class="top-content">
			<view class="top u-f-ac">
				<!-- 头像 -->
				<view class="left">
					<image :src="itemInfo.imgSrc" lazy-load mode="aspectFill"></image>
				</view>
				
				<!-- 标题 -->
				<view class="right">
					#{{itemInfo.title}}#
				</view>
			</view>
			
			<view class="center u-f">
				<view class="new">
					<text space="nbsp"> 动态 {{itemInfo.newNum}} </text>
				</view>
				
				<view class="today">
					<text space="nbsp">  今日 {{itemInfo.today}} </text>
				</view>
			</view>
			
			<view class="bottom">
				{{itemInfo.desc}}
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		props:{
			itemInfo:Object
		}
	}
</script>

<style lang="scss" scoped>
		.content{
			position: relative;
			// 顶部背景图
			.detail-bg{
				height:300rpx;
				width: 100%;
				position: relative;
				image{
					height: 100%;
					width: 100%;
					filter: blur(5rpx);
				}
			}
			
			.top-content{
				padding: 0 30rpx;
				position: relative;
				bottom: 80rpx;
				.top{
					
					.left{
						position: relative;
						image{
							width: 160rpx;
							height: 160rpx;
							border-radius: 16rpx;
						}
					}
					
					.right{
						padding-top:40rpx;
						padding-left: 20rpx;
						font-size: $my-font-size-lg;
					}
				}
				
				.center{
					color:#BBBBBB;
					padding: 10rpx 0;
					.new{
						text{
							margin-right: 20rpx;
						}
					}
				}
				
				.bottom{
					font-size: $uni-font-size-base;
					color:#a3a3a3;
				}
			}
		}
	
</style>
