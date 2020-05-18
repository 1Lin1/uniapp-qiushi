<template>
	<scroll-view scroll-y="true" @scroll="scroll" class="container" >
		<!-- 顶部导航 -->
		<tab-bar 
		:tabBars="tabBars" 
		:tabIndex="tabIndex"
		 @tabClick="tabClick"
		 ></tab-bar>
		 
		
		<!-- 滚动视图 -->
		
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height:swiperHeight *2 + 100 + 'rpx'}" :current="tabIndex" @change="swiperChange">
				<swiper-item v-for="(items,index) in newLists" :key="index">
					<scroll-view scroll-y="true" class="list" @scrolltolower="scrolltolower(index)">
						<template v-if="items.list.length">
							<topic-new :topicNewList="items.list"></topic-new>
						</template>
		
						<!-- 无内容 -->
						<template v-else>
							<no-thing></no-thing>
						</template>
		
					</scroll-view>
		
		
				</swiper-item>
		
			</swiper>
		</view>
	</scroll-view>
</template>

<script>
	import tabBar from '../common/tabBar.vue';
	import noThing from '../common/nothing.vue';
	import topicNew from '../message/topic-new.vue';
	export default {
		components: {
			tabBar,
			noThing,
			topicNew
		},
		props: {

			swiperHeight: {
				type: Number,
				default: 0
			}
		},
		data() {
			return {
				isFixed:true,
				tabIndex: 0,
				newLists: [{
						list: [{
								id: 1001,
								src: '../../static/image/datapic/14.jpg',
								title: '淘宝记录簿',
								desc: '120斤 我的反转人生',
								totalNum: 100,
								todayNum: 10,
							},
							{
								id: 1002,
								src: '../../static/image/datapic/14.jpg',
								title: '淘宝记录簿',
								desc: '120斤 我的反转人生',
								totalNum: 100,
								todayNum: 10,
							},
							{
								id: 1001,
								src: '../../static/image/datapic/14.jpg',
								title: '淘宝记录簿',
								desc: '120斤 我的反转人生',
								totalNum: 100,
								todayNum: 10,
							},
							{
								id: 1002,
								src: '../../static/image/datapic/14.jpg',
								title: '淘宝记录簿',
								desc: '120斤 我的反转人生',
								totalNum: 100,
								todayNum: 10,
							},
							{
								id: 1001,
								src: '../../static/image/datapic/14.jpg',
								title: '淘宝记录簿',
								desc: '120斤 我的反转人生',
								totalNum: 100,
								todayNum: 10,
							},
							{
								id: 1002,
								src: '../../static/image/datapic/14.jpg',
								title: '淘宝记录簿',
								desc: '120斤 我的反转人生',
								totalNum: 100,
								todayNum: 10,
							},
						]
					},

					{
						list: [{
								id: 1003,
								src: '../../static/image/datapic/14.jpg',
								title: '淘宝记录簿',
								desc: '120斤 我的反转人生',
								totalNum: 100,
								todayNum: 10,
							},
							{
								id: 1004,
								src: '../../static/image/datapic/14.jpg',
								title: '淘宝记录簿',
								desc: '120斤 我的反转人生',
								totalNum: 100,
								todayNum: 10,
							},
						]
					},
					{
						list: []
					}
				],
				tabBars: [{
						name: '关注',
						id: 'guanzhu',
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

		methods: {
			tabClick(index) {
				this.tabIndex = index
			},
			
			
			

			//轮播图切换事件
			swiperChange(e) {
				this.tabIndex = e.detail.current
			},

			scrolltolower(index) {
				console.log(11)
				let obj = {
					id: 1001,
					src: '../../static/image/datapic/14.jpg',
					title: '淘宝记录簿',
					desc: '120斤 我的反转人生',
					totalNum: 100,
					todayNum: 10,
				}
				
				uni.showLoading({
					title:'加载中'
				})
				
				setTimeout(() => {
					this.newLists[index].list.push(obj)	
					uni.hideLoading()
				},700)
			}
		}
	}
</script>

<style lang="scss" scoped>
</style>
