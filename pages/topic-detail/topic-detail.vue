<template>
	<view class="topicDetail">

		<!-- 顶部详情信息 -->
		<top-info :itemInfo="topInfo"></top-info>

		<!-- 导航栏 -->
		<tab-bar :tabBars="tabBars" @tabClick="tabClick" :tabIndex="tabIndex" class="tab-bar-set"></tab-bar>

		<!-- 主要内容 -->
		<swiper-content @siwperCg="siwperCg" :swiperHeight="swiperHeight" :list="list" :tabIndex="tabIndex"></swiper-content>


	</view>
</template>

<script>
	import topInfo from '../../components/topic-detail/topInfo.vue';
	import tabBar from '../../components/common/tabBar.vue';
	import swiperContent from '../../components/common/swiper-content.vue';

	export default {
		components: {
			topInfo,
			tabBar,
			swiperContent
		},

		onLoad(options) {

			uni.getSystemInfo({
				success: (res) => {
					// 动态获取手机屏幕高度
					this.swiperHeight = res.windowHeight;
					console.log(this.swiperHeight)
				}
			});

		},

		


		data() {
			return {
				tabIndex: 0,
				swiperHeight: 0,
				tabBars: [{
						name: '默认',
						id: 'default',
					},
					{
						name: '最新',
						id: 'new'
					}
				],
				list: {
					// 文字
					new:[
						{
							id: "2001",
							userpic: "../../static/image/topicpic/12.jpeg", //头像
							username: "我是大大大王",
							sex: 0, // 0 男 1女
							age: 25,
							isGuanzhu: true,
							title: "我是文字的标题",
							titlePic: "", //封面图
							picContent: "", //图文列表图片
							viedo: "", //视频
							share: "", //分享
							address: "深圳 龙岗",
							shareNum: 10,
							commentNum: 999,
							goodNum: 888
						},
						
						//图文
						{
							id: "2002",
							userpic: "../../static/image/topicpic/12.jpeg", //头像
							username: "我是大大大王",
							sex: 0, // 0 男 1女
							age: 25,
							isGuanzhu: false,
							title: "我是图文的标题",
							titlePic: "../../static/image/datapic/13.jpg", //封面图
							picContent: "", //图文列表图片 暂时一张
							viedo: "", //视频
							share: "", //分享
							address: "深圳 龙岗",
							shareNum: 10,
							commentNum: 999,
							goodNum: 888
						},
						//视频
						{
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
						},
						
						//分享
						{
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
					],

					default:[
						//视频
						{
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
						},
						
						//分享
						{
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
						},
						//视频
						{
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
						},
						
						//分享
						{
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
						},
					]
				},
				topInfo: {
					'bg': '../../static/image/datapic/41.jpg',
					'imgSrc': '../../static/image/datapic/41.jpg',
					'title': '忆往事，敬余生',
					'newNum': 999,
					'today': 11,
					'desc': '面试官: 在电梯里巧遇马云你会做什么？90后女孩的回答当场被录用'
				}
			};
		},
		methods: {
			// 导航切换
			tabClick(index) {
				this.tabIndex = index;
			},


			//轮播图切换
			siwperCg(index) {
				this.tabIndex = index;
			}
		},
		
		//监听下拉刷新
		onPullDownRefresh() {
			console.log('refresh');
			setTimeout(() => {
				
				// this.list.splice(0,1)
				uni.stopPullDownRefresh();
			}, 1000);
		},


	}
</script>

<style lang="scss" scoped>
	.topicDetail {
		height: 100%;
	}

	.tab-bar-set {
		text-align: center;
	}
</style>
