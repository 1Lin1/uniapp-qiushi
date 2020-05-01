<template>
	<view>
		<!-- 自定义导航栏 -->
	<uni-nav-bar 
		class="uni-nav-bar"
		:statusBar="true" 
		>
		<!-- 左边 -->
		<block slot="left">
			<view class="icon-left-right nav-left">
				<view class="icon iconfont icon-qiandao">
					
				</view>
			</view>
		</block>
		<!-- 中间 -->
		<view class="nav-center u-f-ajc">
			<view v-for="(item,index) in tabBars" :key="item.id" class="title" @tap="tabChange(index)">
				<text :class="{activeTabItem:tabIndex === index}">{{item.name}}</text>
			</view>
		</view>
		<!-- 右边 -->
		<block slot="right">
			<view class="icon-left-right">
				<view class="icon iconfont icon-bianji1">
					
				</view>
			</view>
		</block>
	</uni-nav-bar>
	
	<view class="content-msg u-f-ajc">
		<view class="msg-left">
			<image src="../../static/image/topicpic/12.jpeg" mode="widthFix"></image>
		</view>
		
		<view class="msg-right">
			<view class="top u-f-ajs">
				<view class="left u-f-ajc">
					<view class="name">昵称</view>
					<view class="ageSex icon iconfont icon-nan">25</view>
				</view>
				<view class="right u-f-ajc">
					<view class="focus icon iconfont icon-zengjia">关注</view>
					<view class="icon iconfont icon-guanbi"></view>
				</view>
			</view>
			
			<view class="title">
				aaaa啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊
			</view>
			
			<view class="content">
				<image src="../../static/image/datapic/13.jpg" mode="widthFix"></image>
			</view>
			
			<view class="bottom">
				
			</view>
		</view>
	</view>
	
	</view>
</template>

<script>
	import uniNavBar from '../../components/uni-nav-bar/uni-nav-bar.vue'
	export default {
		components:{
		},
		data() {
			return {
				tabBars:[
					{name:'关注',id:'focus'},
					{name:'话题',id:'topic'},
				],
				tabIndex:0,
			}
		},
		methods: {
			tabChange(index){
				this.tabIndex = index;
			}
		}
	}
</script>

<style lang="scss" scoped>
	
	// 顶部导航栏
	.uni-nav-bar{
		
		// 签到图标
		.icon-qiandao{
			color:#FEE42A
		}
		.nav-left{
			margin-left: 40upx;
		}
		.nav-center{
			width: 100%;
			height: 100%;
			.title{
				text{
					padding: 8upx 34upx;
					font-size: 34upx;
					color: #969696;
					font-weight: bold;
				}
			}
		}
		.icon-left-right{
			.icon{
				font-size: 54upx;
			}
		}
	}
	
	
	// 内容
	.content-msg{
		padding: 20upx;
		.msg-left{
			align-self: flex-start;
			image{
				width: 90upx;height: 90upx;
				border-radius: 100%;
			}
		}
		
		.msg-right{
			margin-left: 10upx;
			image{
				width: 100%;
			}
		}
	}
	//顶部导航栏激活
	.activeTabItem{
		color:#000000 !important;
		border-bottom: 4upx solid #ffff00;
	}

</style>
