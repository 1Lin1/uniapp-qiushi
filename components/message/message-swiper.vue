<template>
	<view>
		
		<!-- 自定义导航栏 -->
		<uni-nav-bar 
			class="uni-nav-bar"
			:statusBar="true" 
			:fixed="true"
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
		
		<view class="uni-tab-bar" >
			<swiper class="swiper-box"
			:style="{height:swiperHeight *2 + 100 + 'rpx'}"
			:current="tabIndex"
			@change="swiperChange"
			>
				<!-- 关注 -->
				<swiper-item>
					<scroll-view scroll-y="true" class="list" @scrolltolower="scrolltolower(tabIndex)">
						<block v-for="(item,index) in list" :key="item.id">
							<message-list :item="item"></message-list>
						</block>
						
					</scroll-view>
				</swiper-item>
				
				<!-- 话题 -->
				<swiper-item >
					<scroll-view scroll-y="true" class="list" @scrolltolower="scrolltolower(tabIndex)" >
						<topic-list :topicNewList="topicNewList"></topic-list>
					</scroll-view>
				</swiper-item>
				
			</swiper>
		</view>
	
	</view>
</template>

<script>
	import messageList from '../../components/message/message-list.vue';
	import uniNavBar from '../../components/uni-nav-bar/uni-nav-bar.vue';
	import topicList from './topic-list.vue';
	export default{
		components:{
			uniNavBar,
			messageList,
			topicList
		},
		props:{
			swiperHeight:Number,
		},
		data(){
			return {
				tabBars:[
					{name:'关注',id:'focus'},
					{name:'话题',id:'topic'},
				],
				tabIndex:0,
				// 关注列表
				list:[
					// 文字
					{
						id:"2001",
						userpic:"../../static/image/topicpic/12.jpeg",//头像
						username:"我是大大大王",
						sex:0,// 0 男 1女
						age:25,
						isGuanzhu:true,
						title:"我是文字的标题",
						titlePic:"",//封面图
						picContent:"",//图文列表图片
						viedo:"", //视频
						share:"", //分享
						address:"深圳 龙岗",
						shareNum:10,
						commentNum:999,
						goodNum:888
					},
					
					//图文
					{
						id:"2002",
						userpic:"../../static/image/topicpic/12.jpeg",//头像
						username:"我是大大大王",
						sex:0,// 0 男 1女
						age:25,
						isGuanzhu:false,
						title:"我是图文的标题",
						titlePic:"../../static/image/datapic/13.jpg",//封面图
						picContent:"",//图文列表图片 暂时一张
						viedo:"", //视频
						share:"", //分享
						address:"深圳 龙岗",
						shareNum:10,
						commentNum:999,
						goodNum:888
					},
					
					//视频
					{
						id:"2003",
						userpic:"../../static/image/topicpic/12.jpeg",//头像
						username:"我是大大大王",
						sex:1,// 0 男 1女
						age:25,
						isGuanzhu:false,
						title:"我是视频的标题",
						titlePic:"../../static/image/datapic/13.jpg",//封面图
						picContent:"",//图文列表图片 暂时一张
						viedo:{
							playNum:"20w",
							timeLong:"2:47"
						}, //视频
						share:"", //分享
						address:"深圳 龙岗",
						shareNum:10,
						commentNum:999,
						goodNum:888
					},
					
					//分享
					{
						id:"2004",
						userpic:"../../static/image/topicpic/12.jpeg",//头像
						username:"我是大大大王",
						sex:0,// 0 男 1女
						age:25,
						isGuanzhu:false,
						title:"我是分享的标题",
						titlePic:"",//封面图
						picContent:"",//图文列表图片 暂时一张
						viedo:"", //视频
						share:{
							sharePic:"../../static/image/datapic/14.jpg",
							shareTitle:"我是分享图的右边内容"
						}, //分享
						address:"深圳 龙岗",
						shareNum:10,
						commentNum:999,
						goodNum:888
					},
				],
				
				// 话题列表
				topicNewList:[
						{
							id:1001,
							src:'../../static/image/datapic/14.jpg',
							title:'淘宝记录簿',
							desc:'120斤 我的反转人生',
							totalNum:100,
							todayNum:10,
						},
						{
							id:1002,
							src:'../../static/image/datapic/14.jpg',
							title:'淘宝记录簿',
							desc:'120斤 我的反转人生',
							totalNum:100,
							todayNum:10,
						},
						{
							id:1003,
							src:'../../static/image/datapic/14.jpg',
							title:'淘宝记录簿',
							desc:'120斤 我的反转人生',
							totalNum:100,
							todayNum:10,
						},
						{
							id:1004,
							src:'../../static/image/datapic/14.jpg',
							title:'淘宝记录簿',
							desc:'120斤 我的反转人生',
							totalNum:100,
							todayNum:10,
						},
					]
			}
		},
		methods:{
			//轮播图切换事件
				swiperChange(e){
					this.tabIndex = e.detail.current
					console.log(this.tabIndex)
				},
				//导航点击事件
				tabChange(index){
					this.tabIndex = index;
				},
				
				//触地事件
				scrolltolower(tabIndex){
					console.log('scrolltolower' +  tabIndex);
					// 通过下标分辨关注和话题
					
					if(tabIndex === 0){
						let obj = {
							id:"2005",
							userpic:"../../static/image/topicpic/12.jpeg",//头像
							username:"我是大大大王",
							sex:1,// 0 男 1女
							age:25,
							isGuanzhu:false,
							title:"我是视频的标题",
							titlePic:"../../static/image/datapic/13.jpg",//封面图
							picContent:"",//图文列表图片 暂时一张
							viedo:{
								playNum:"20w",
								timeLong:"2:47"
							}, //视频
							share:"", //分享
							address:"深圳 龙岗",
							shareNum:10,
							commentNum:999,
							goodNum:888
						}
						
						uni.showLoading({
							title:'加载中'
						})
						
						setTimeout(() => {
							this.list.push(obj);
							uni.hideLoading()
						},500)
					}
				}
		}
	}
</script>

<style lang="scss" scoped>
	// 顶部导航栏
	.uni-nav-bar{
		width: 100%;
		// 签到图标
		.icon-qiandao{
			color:#FEE42A
		}
		.nav-left{
			margin-left: 40rpx;
		}
		.nav-center{
			width: 100%;
			height: 100%;
			.title{
				text{
					padding: 8rpx 34rpx;
					font-size: 34rpx;
					color: #969696;
					font-weight: bold;
				}
			}
		}
		.icon-left-right{
			.icon{
				font-size: 54rpx;
			}
			.top{
				
			}
		}
	}
	
	
	
	//顶部导航栏激活
	.activeTabItem{
		color:#000000 !important;
		border-bottom: 6rpx solid #ffff00;
	}
</style>
