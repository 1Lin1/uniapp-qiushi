<template>
	<view class="uni-tab-bar">

		<swiper class="swiper-box" :style="{height:swiperHeight *2 + 'rpx'}" :current="tabIndex" @change="swiperChange">
			
			<!-- 默认 -->
			<swiper-item>
				<!-- 导航栏 -->

				<scroll-view scroll-y="true" class="list"
				 @scrolltolower="scrolltolower(tabIndex)"
				 @scroll="scroll"
				 :scroll-top="scrollTop"
				   >
					<block v-for="(item,index) in list.default" :key="index">
						<message-list :item="item"></message-list>
					</block>

				</scroll-view>
			</swiper-item>

			<!-- 最新 -->
			<swiper-item>

				<scroll-view scroll-y="true" class="list"
				 @scrolltolower="scrolltolower(tabIndex)"
				 @scroll="scroll"
				 :scroll-top="scrollTop"
				   >
					<block v-for="(item,index) in list.new" :key="index">
						<message-list :item="item"></message-list>
					</block>
				
				</scroll-view>
			</swiper-item>

		</swiper>

		<scroll-to-top v-show="isShowTop" @click.native="backToTop"></scroll-to-top>
	</view>
</template>

<script>
	import messageList from '../../components/message/message-list.vue';
	import scrollToTop from './scrollToTop.vue';
	export default {
		components: {
			messageList,
			scrollToTop
		},
		props: {
			swiperHeight: Number,
			tabIndex: Number,
			list:Object,
		},
		data() {
			return {
				
				scrollTop: 0,
				old: {
					scrollTop: 0
				},
				isShowTop: false,
				
			}
		},

		methods: {
			//轮播图切换事件
			swiperChange(e) {
				this.$emit('siwperCg', e.detail.current)
			},

			//触地事件
			scrolltolower(tabIndex) {
				console.log('scrolltolower' + tabIndex);
				// 通过下标分辨关注和话题
	
				uni.showLoading({
					title: '加载中'
				})
				
				if (tabIndex === 0) {
					let obj = {
						id: "2003",
						userpic: "../../static/image/topicpic/12.jpeg", //头像
						username: "我是大大大王",
						sex: 1, // 0 男 1女
						age: 25,
						isGuanzhu: false,
						title: "我是视频的标题",
						titlePic: "../../static/image/datapic/13.jpg", //封面图
						picContent: "", //图文列表图片 暂时一张
						viedo: {
							playNum: "20w",
							timeLong: "2:47"
						}, //视频
						share: "", //分享
						address: "深圳 龙岗",
						shareNum: 10,
						commentNum: 999,
						goodNum: 888
					}

					setTimeout(() => {
						this.list.default.push(obj);
						uni.hideLoading()
					}, 1500)
				} else {
					let obj = {
							id: "2004",
							userpic: "../../static/image/topicpic/12.jpeg", //头像
							username: "我是大大大王",
							sex: 0, // 0 男 1女
							age: 25,
							isGuanzhu: false,
							title: "我是分享的标题",
							titlePic: "", //封面图
							picContent: "", //图文列表图片 暂时一张
							viedo: "", //视频
							share: {
								sharePic: "../../static/image/datapic/14.jpg",
								shareTitle: "我是分享图的右边内容"
							}, //分享
							address: "深圳 龙岗",
							shareNum: 10,
							commentNum: 999,
							goodNum: 888
						}
						setTimeout(() => {
							this.list.new.push(obj);
							uni.hideLoading()
						}, 1500)
				}
			
				
			},



			//滚动监听
			scroll(e) {
				this.old.scrollTop = e.detail.scrollTop;
				this.isShowTop = e.detail.scrollTop > 300;

			},


			
			//回到顶部
			backToTop() {
				this.scrollTop = this.old.scrollTop
				this.$nextTick(() => {
					this.scrollTop = 0
				});
				uni.showToast({
					title: "回到顶部"
				})
			}

		}
	}
</script>

<style lang="scss" scoped>
	
	.uni-tab-bar{
		width: 100%;
	}
	.tab-bar-set {
		text-align: center;
	}
</style>
