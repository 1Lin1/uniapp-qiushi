<template>
	<view class="uni-tab-bar">
		<scroll-view id="tab-bar"  :scroll-x="true" class="uni-swiper-tab" >
		   <block v-for="(item,index) in tabBars" :key="item.id">
			   <view class="swiper-tab-list" @tap="tabClick(index)">
					<text :class="{activeTabItem:tabIndex === index ? true : ''}">
						{{item.name}}
					</text>
					
			   </view>
		   </block>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		props:{
			tabBars:Array,
			tabIndex:Number,
		},
		data(){
			return{
			}
		},
		methods:{
			//顶部导航栏点击
			tabClick(index){
				this.$emit('tabClick',index)
			}
		},
	}
</script>

<style lang="scss" scoped>
	.uni-tab-bar{
		.swiper-tab-list{
			text {
				padding: 14upx;
				font-size: 34upx;
				color: #000000;
				font-weight: bold;
			}
		}
	}
	
	//顶部导航栏激活
	.activeTabItem{
		border-bottom: 6upx solid #ffff00;
	}
</style>
