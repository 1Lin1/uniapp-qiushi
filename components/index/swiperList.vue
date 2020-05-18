<template>
	<view>
		
		<!-- 顶部导航栏点击 -->
		<tab-bar :tabBars="tabBars" @tabClick="tabClick" :tabIndex="tabIndex"></tab-bar>
		
		<!-- 滚动视图 -->
		
		<view class="uni-tab-bar">
			<swiper class="swiper-box" 
			:style="{height:swiperHeight *2 + 'rpx'}" 
			:current="tabIndex"
			@change="swiperChange"
			>
				<swiper-item v-for="(items,index) in newLists" :key="index">
						<scroll-view scroll-y="true" class="list" @scrolltolower="scrolltolower(index)">
							<template v-if="items.list.length">
								<block v-for="(item,index2) in items.list" :key="index2" >
									<indexlist :item="item" ></indexlist>
								</block>
							</template>
							
							<!-- 无内容 -->
							<template v-else>
								<no-thing></no-thing>
							</template>
							
						</scroll-view>
					
					>
					
				</swiper-item>
				
			</swiper>
			
		</view>
	</view>
</template>

<script>
	import indexlist from './index-list.vue';
	import tabBar from '../common/tabBar.vue';
	import noThing from '../common/nothing.vue'
	export default {
		props:{
		
			swiperHeight:{
				type:Number,
				default:0
			}
		},
		components:{
			indexlist,
			tabBar,
			noThing
		},
		data(){
			return {
				tabIndex:0,
				newLists:[
					{
						list:[
							{
								id:'10001',
								userpic:"../../static/image/topicpic/11.jpeg",//用户头像
								username:"Mike", //用户名
								isGuanzhu:true,
								title:"如何通过手账改变生活",
								type:"img",
								titleImage:"../../static/image/datapic/11.jpg",//封面图
								infoNum:{
									cNum:1,//0:不操作 1:顶 2::踩
									dingNum:11,
									caiNum:5
								},
								commentNum:10,
								shareNum:11
							},
							
							{
								id:'10002',
								userpic:"../../static/image/topicpic/11.jpeg",//用户头像
								username:"Rose", //用户名
								isGuanzhu:false,
								title:"如何通过手账改变生活",
								type:"video",
								titleImage:"../../static/image/datapic/11.jpg",//封面图
								infoNum:{
									playNum:"20w	",
									time:"2:00",
									cNum:0,//0:不操作 1:顶 2::踩
									dingNum:11,
									caiNum:5
								},
								commentNum:10,
								shareNum:11
							},
						]
					},
					
					{
						list:[
							{
								id:'10003',
								userpic:"../../static/image/topicpic/11.jpeg",//用户头像
								username:"Mike", //用户名
								isGuanzhu:true,
								title:"如何通过手账改变生活",
								type:"img",
								titleImage:"../../static/image/datapic/11.jpg",//封面图
								infoNum:{
									cNum:1,//0:不操作 1:顶 2::踩
									dingNum:11,
									caiNum:5
								},
								commentNum:10,
								shareNum:11
							},
							
							{
								id:'10004',
								userpic:"../../static/image/topicpic/11.jpeg",//用户头像
								username:"Rose", //用户名
								isGuanzhu:false,
								title:"如何通过手账改变生活",
								type:"video",
								titleImage:"../../static/image/datapic/11.jpg",//封面图
								infoNum:{
									playNum:"20w	",
									time:"2:00",
									cNum:2,//0:不操作 1:顶 2::踩
									dingNum:11,
									caiNum:5
								},
								commentNum:10,
								shareNum:11
							},
						]
					},
					{
						list:[]
					}
				],
				tabBars:[
					{	name:'关注',
						id:'guanzhu',
					},
					{
					    name: '推荐',
					    id: 'tuijian'
					}, {
					    name: '体育',
					    id: 'tiyu'
					}, {
					    name: '热点',
					    id: 'redian'
					}, {
					    name: '财经',
					    id: 'caijing'
					}, {
					    name: '娱乐',
					    id: 'yule'
					}, {
					    name: '军事',
					    id: 'junshi'
					}, 
				],
			}
		},
		
		methods:{
			
			tabClick(index){
				this.tabIndex = index
			},
			//轮播图切换事件
			swiperChange(e){
				this.tabIndex = e.detail.current
			},
			
			// 下拉到底部
			scrolltolower(index){
				let obj = {
						id:'10007',
						userpic:"../../static/image/topicpic/11.jpeg",//用户头像
						username:"Mike", //用户名
						isGuanzhu:true,
						title:"如何通过手账改变生活",
						type:"img",
						titleImage:"../../static/image/datapic/11.jpg",//封面图
						infoNum:{
							cNum:1,//0:不操作 1:顶 2::踩
							dingNum:11,
							caiNum:5
						},
						commentNum:10,
						shareNum:11
				}
				
				uni.showLoading({
					title:'加载中'
				})
				
				setTimeout(() => {
					this.newLists[index].list.push(obj)
					console.log(this.newLists[index].list)
					uni.hideLoading()
				},500)
			}
		}
	}
</script>

<style lang="scss" scoped>
	.uni-tab-bar{
		.swiper-tab-list{
			text {
				padding: 8rpx;
				font-size: 34rpx;
				color: #000000;
				font-weight: bold;
			}
		}
	}
	
	//顶部导航栏激活
	.activeTabItem{
		border-bottom: 6rpx solid #ffff00;
	}
	
	.loadMore{
		padding: 10rpx;
		text-align: center;
		color: #aaaaaa;
	}
</style>
