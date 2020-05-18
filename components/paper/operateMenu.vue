<template>
	<view class="right-popup" v-show="isShowOperate">
		<view class="top u-f-ac">
			<view class="icon iconfont icon-sousuo">
				
			</view>
			<view class="text">
				加糗友
			</view>
		</view>	
		
		<view class="bottom u-f-ac" @tap="toClearAll">
			<view class="icon iconfont icon-qingchu">
				
			</view>
			<view class="text">
				清除已读
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			isShowOperate:Boolean,//展示操作菜单
		},
		data(){
			return {
				
			}
		},
		methods:{
			//清除已读
			toClearAll(){
				this.$emit('toClearAll');
			}
		},
		
	}
</script>

<style lang="scss" scoped>
	.right-popup{
		background-color:#FFFFFF;
		z-index: 999;
		border: 1rpx solid #EEEEEE;
		right: 0;
		top: 105rpx;
		position: fixed;
		width: 55%;
		height: 200rpx;
		display: flex;
		flex-wrap: wrap;
		padding: 20rpx;
		
		
		box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1);
		.top,.bottom{
			.icon {
				font-size: $my-font-size-lg;
				font-weight: 530;
				margin-right: 40rpx;
			}
			.text{
				font-size: $my-font-size-lg;
			}
		}
	}
</style>
