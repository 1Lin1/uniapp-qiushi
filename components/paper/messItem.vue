<template>
		<view class="content u-f-ajc animated fadeInLeft">
			<!-- //头像 -->
			<view class="left">
				<image :src="messItem.userpic" lazy-load></image>
			</view>
			
			<!-- 有半部分 -->
			<view class="right">
				<view class="top u-f-ajs">
					<!-- 用户名 -->
					<view class="username">
						{{messItem.userName}}
					</view>
					
					<!-- 时间 -->
					<view class="time">
						{{messItem.time}}
					</view>
				</view>
				
				
				<view class="bottom u-f-ajs">
					<!-- 消息 -->
					<view class="message">
						{{messItem.data}}
					</view>
					
					<!-- 角落图标 -->
					<view class="badge">
						<uni-badge class=" badge uni-badge-left-margin" :text="messItem.badgeNum" type="error" />
					</view>
				</view>
			</view>
		</view>
</template>

<script>
	import uniBadge from '../../components/uni-badge/uni-badge.vue';
	export default{
		components:{
			uniBadge
		},
		props:{
			messItem:Object
		}
	}
</script>
<style lang="scss" scoped>
	
		.content{
			border-bottom: 1rpx solid #EEEEEE;
			padding: 10rpx;
			.left{
				flex:2;
				flex-shrink: 0;
				text-align: center;
				height: 120rpx;
				line-height: 120rpx;
				image{
					width: 120rpx;
					height: 120rpx;
					border-radius: 50%;
				}
				
			}
			
			.right{
				flex: 8;
				.top{
					.username{
						font-size: $my-font-size-lg;
					}
					.time{
						color:#cdcdcd;
					}
				}
				
				.bottom{
					.message{
						font-size: $uni-font-size-lg;
						color:#aaaaaa;
					}
					.badge{
					
					}
				}
			}
		}
</style>
