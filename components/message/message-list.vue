<template>
	<view class="content-msg u-f-ajc animated rotateInDownLeft">
		
		<!-- 左边用户头像 -->
		<view class="msg-left">
			<image :src="item.userpic" mode="widthFix"></image>
		</view>
		
		<!-- 右边基本信息 -->
		<view class="msg-right">
			<view class="top u-f-ajs">
				<view class="left u-f-ajc">
					<view class="name">{{item.username}}</view>
					<view class="ageSex icon iconfont" :class="item.sex == 0 ? 'icon-nan':'icon-nv'">
					{{item.age}}
					</view>
				</view>
				<view class="right u-f-ajc">
					<view class="focus" >
						<button
						  class="icon iconfont icon-zengjia"
						  size="mini"
						  :disabled="isGuanzhu"
						  @tap="focusClick"
						   >
							<text>关注</text>
						</button>
					</view>
				</view>
			</view>
			
			<view class="title">
				<text>{{item.title}}</text>
			</view>
			
			<template v-if="item.titlePic || item.share">
				<view class="content u-f-ajc">
					
					<template v-if="item.titlePic">
						<!-- 图片 -->
						<image src="../../static/image/datapic/13.jpg" mode="widthFix" lazy-load=""></image>
						
						<template v-if="item.viedo">
							<!-- 视频 -->
							<view class="video-play icon iconfont icon-bofang">
							</view>
							<view class="video-play play-info">
								{{item.viedo.playNum}}次播放  {{item.viedo.timeLong}}
							</view>
						</template>
					</template>
					
					<!-- 分享 -->
					<template v-if="item.share">
						<view class="content-list-share u-f-ajc">
							<view class="left-img">
								<image :src="item.share.sharePic" mode="widthFix" lazy-load></image>
							</view>
							<view class="right-title">
								{{item.share.shareTitle}}
							</view>
						</view>
					</template>
				</view>
			</template>
			
			<view class="bottom u-f-ajs">
				<view class="b-left">
					<view class="address">
						{{item.address}}
					</view>
				</view>
				
				<view class="b-right u-f-aje">
					<view class="icon iconfont icon-zhuanfa">
						{{item.shareNum}}
					</view>
					
					<view class="icon iconfont icon-pinglun1">
						{{item.commentNum}}
					</view>
					
					<view class="icon iconfont icon-ccdbaa">
						{{item.goodNum}}
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		props:{
			item:{
				type:Object,
				default: {}
			}
		},
		data(){
			return {
				isGuanzhu:this.item.isGuanzhu
			}
		},
		methods:{
			//关注点击
			focusClick(){
				this.isGuanzhu = true;
				uni.showToast({
					title:'关注成功'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	
	// 内容
	.content-msg{
		padding: 20rpx;
		border-bottom: 1upx solid #EEEEEE;
		.msg-left{
			align-self: flex-start;
			flex-shrink: 0;
			flex:1;
			image{
				width: 90rpx;height: 90rpx;
				border-radius: 100%;
			}
		}
		
		.msg-right{
			flex: 9;
			margin-left: 10rpx;
			image{
				width: 100%;
			}
			
			.top{
				.left{
					.name{
						font-size: $uni-font-size-base;
						color: #BBBBBB;
					}
					.ageSex{
						color: #FFFFFF;
						padding: 0 6rpx;
						font-size: 20rpx;
						line-height: 24rpx;
						border-radius: 20rpx;
						
					}
					.icon-nan{
						background-color: #007AFF;
					}
					
					.icon-nv{
						background-color: #FC427B;
					}
				}
				.right{
					.focus{
						font-size: $uni-font-size-sm;
						line-height: $uni-font-size-sm;
					}
				}
			}
			.title{
				font-size: $uni-font-size-lg;
				font-weight: bold;
			}
			
			// 视频
			.content{
				position: relative;
				.icon-bofang{
					color: #FFFFFF;
					font-size: $bofang-font-size;
				}
				.video-play{
					position: absolute;
				}
				.play-info{
					padding: 0 4rpx;
					right: 20rpx;
					bottom: 10rpx;
					color: #FFFFFF;
					font-size: 20rpx;
					border-radius: 25rpx;
					background-color: rgba(51, 51, 51, 0.8);
				}
				
				// 分享图文
				.content-list-share{
					background-color: #F7F7F7;
					width: 100%;
					padding: 20rpx 20rpx 10rpx 20rpx;
					.left-img{
						width: 120rpx;
						flex: 4;
						image{
							width: 100%;
						}
					}
					.right-title{
						font-size: $uni-font-size-base;
						font-weight: bolder;
						flex:6;
						margin-left: 20rpx;
						align-self:flex-start;
					}
				}
			}
			
			.bottom{
				padding-top:16rpx;
				color:#BBBBBB;
				.b-left{
					flex:4;
				}
				.b-right{
					flex:6;
					.iconfont{
						font-size: $uni-font-size-base;
					}
				}
			}
		}
	}
</style>
