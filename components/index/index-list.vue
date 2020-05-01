<template>
	<view class="content animated rotateInDownLeft">
		<view class="top">
			<view class="tou-xiang">
				<image :src="item.userpic" mode="widthFix"></image>
			</view>
			<view class="username">
				<text>{{item.username}}</text>
			</view>

			<view class="watch">
				<button 
				  class="icon iconfont icon-zengjia"
				  :disabled="isGuanzhu"
				  @tap="guanZhuClick"
				   >
					<text>关注</text>
				</button>
			</view>
			<view class="icon iconfont icon-guanbi">

			</view>
		</view>

		<view class="center">
			<view class="content-title">
				<text>{{item.title}}</text>
			</view>
			<view class="content-image">

				<view class="videoStyle" v-show="item.type === 'video'">
					<view class="icon iconfont icon-bofang">
					</view>
					<view class="bofang-num">
						{{infoNum.playNum}}次播放 {{infoNum.time}}
					</view>
				</view>


				<image :src="item.titleImage" mode="widthFix">
				</image>

			</view>
		</view>

		<view class="bottom">
			<view class="icon-left">
				<view class="icon iconfont icon-icon_xiaolian-mian" 
				:class="{active:infoNum.cNum == 1 ? true :false}"
				@tap="operate('ding')"
				>
				</view>
				<view class="xiao-num" >
					{{infoNum.dingNum}}
				</view>

				<view class="icon iconfont icon-kulian" 
				:class="{active:infoNum.cNum == 2 ? true :false}"
				@tap="operate('cai')"
				>
				</view>
				<view class="ku-num" >
					{{infoNum.caiNum}}
				</view>
			</view>
			<view class="icon-right">

				<view class="icon iconfont icon-pinglun1">
				</view>
				<view class="comment">
					{{item.commentNum}}
				</view>

				<view class="icon iconfont icon-zhuanfa">
				</view>
				<view class="zhuan-fa">
					{{item.shareNum}}
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			item: {
				type: Object,
				default: {}
			}
		},
		data() {
			return {
				isGuanzhu:this.item.isGuanzhu,
				infoNum:this.item.infoNum,
			};
		},
		methods:{
			//关注操作
			guanZhuClick(){
				uni.showToast({
					title:'关注成功',
					icon:'success'
				})
				this.isGuanzhu = true
			},
			
			//顶踩操作
			operate(type){
				switch(type){
					case 'ding':
						if(this.infoNum.cNum == 1)
						 {
						     return ; 
						 }
						this.infoNum.dingNum ++;
						if(this.infoNum.cNum !== 0){
							this.infoNum.caiNum --;
						}
						this.infoNum.cNum = 1;
						break;
					case 'cai':
						if(this.infoNum.cNum == 2)  {
						     return ; 
						 }
						this.infoNum.caiNum ++;
						
						//若无进行 操作
						if(this.infoNum.cNum !== 0){
							this.infoNum.dingNum --;
						}
						this.infoNum.cNum = 2;
						break;
				}
			}
		}
	}
</script>

<style lang="scss" scoped>
	.content {
		// margin-top: 88upx;
		padding: 30upx;
		border-bottom: 1upx solid #CCCCCC;

		.top {
			display: flex;
			justify-content: space-between;
			align-items: center;

			.tou-xiang {
				image {
					width: 100upx;
					height: 100upx;
					border-radius: 50%;
				}
			}

			.username {
				font-size: $uni-font-size-lg;
				margin-right: 280upx;
				color: $uni-text-color-grey;
			}
			.watch{
				button{
					text{
						font-size: 30upx;
					}
				}
			}
		}

		.center {
			.content-title {
				font-size: 40upx;
				font-weight: bolder;
			}

			.content-image {
				position: relative;

				image {
					position: relative;
					width: 100%;
					border-radius: 20upx;
				}

				.videoStyle {

					// position: relative;
					.bofang-num {
						width: 220upx;
						height: 50upx;
						line-height: 50upx;
						text-align: center;
						position: absolute;
						right: 20upx;
						bottom: 20upx;
						color: #FFFFFF;
						background-color: rgba(51, 51, 51, 0.72);
						border-radius: 40upx;
						z-index: 1;
					}

					.icon-bofang {
						position: absolute;
						font-size: 140upx;
						left: 40%;
						top: 20%;
						color: #FFFFFF;
						z-index: 999;
					}
				}

			}


		}

		.bottom {
			display: flex;
			justify-content: space-between;

			.icon-left,
			.icon-right {
				display: flex;
				flex: 0.3;
				justify-content: space-evenly;
				color: $uni-text-color-grey;
			}
		}
	}

	.iconfont {
		font-size: $uni-font-size-base;
	}
	
	.active{
		color:#FEE42A
	}
</style>
