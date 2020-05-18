<template>
	<view class="paper">
		
		<!-- 操作菜单 -->
		<operate-menu @toClearAll="toClearAll" :isShowOperate="isShowOperate"></operate-menu>
		
		
		<!-- 信息列表 -->
		<mess-box :messList="messList"></mess-box>
	</view>
</template>

<script>
	import messBox from '../../components/paper/messBox.vue';
	import operateMenu from '../../components/paper/operateMenu.vue';
	export default {
		components: {
			messBox,
			operateMenu
		},
		data() {
			return {
				isShowOperate:false,
				messList: [{
						userpic: '../../static/image/topicpic/1.jpeg',
						userName: 'MIKE',
						time: '13:21',
						data: '消息1',
						badgeNum: 10
					},
					{
						userpic: '../../static/image/topicpic/2.jpeg',
						userName: 'ROSE',
						time: '14:21',
						data: '消息2',
						badgeNum: 9
					},
					{
						userpic: '../../static/image/topicpic/3.jpeg',
						userName: 'JACK',
						time: '18:21',
						data: '消息3',
						badgeNum: 17
					},
				]
			}
		},
		methods: {
			toClearAll(){
				this.messList = [];
				this.isShowOperate = false;
				uni.showToast({
					title:'已清空'
				})
			}
		},
		
		//操作菜单
		onNavigationBarButtonTap(e){
			if(e.index == 1){
				this.isShowOperate = !this.isShowOperate;
			}else{
				// 跳转到好友列表
				uni.navigateTo({
					url:'../user-list/user-list'
				})
			}
		},
		//触底加载
		onReachBottom() {
			uni.showLoading({
				title: '加载中'
			})

			setTimeout(() => {
				let obj = {
					userpic: '../../static/image/topicpic/1.jpeg',
					userName: 'MIKE',
					time: '13:21',
					data: '消息1',
					badgeNum: 100
				}
				this.messList.push(obj)
				uni.hideLoading()
			}, 500)
		},
		
		
		//下拉树新
		onPullDownRefresh() {
			console.log('refresh');
			setTimeout(() => {
				this.messList = [{
						userpic: '../../static/image/topicpic/1.jpeg',
						userName: 'MIKE',
						time: '13:21',
						data: '消息1',
						badgeNum: 100
					},
					{
						userpic: '../../static/image/topicpic/2.jpeg',
						userName: 'ROSE',
						time: '14:21',
						data: '消息2',
						badgeNum: 90
					},
					{
						userpic: '../../static/image/topicpic/3.jpeg',
						userName: 'JACK',
						time: '18:21',
						data: '消息3',
						badgeNum: 170
					},
					{
						userpic: '../../static/image/topicpic/1.jpeg',
						userName: 'MIKE',
						time: '13:21',
						data: '消息1',
						badgeNum: 100
					},
					{
						userpic: '../../static/image/topicpic/2.jpeg',
						userName: 'ROSE',
						time: '14:21',
						data: '消息2',
						badgeNum: 90
					},
					{
						userpic: '../../static/image/topicpic/3.jpeg',
						userName: 'JACK',
						time: '18:21',
						data: '消息3',
						badgeNum: 170
					},
					{
						userpic: '../../static/image/topicpic/1.jpeg',
						userName: 'MIKE',
						time: '13:21',
						data: '消息1',
						badgeNum: 100
					},
					{
						userpic: '../../static/image/topicpic/2.jpeg',
						userName: 'ROSE',
						time: '14:21',
						data: '消息2',
						badgeNum: 90
					},
					{
						userpic: '../../static/image/topicpic/3.jpeg',
						userName: 'JACK',
						time: '18:21',
						data: '消息3',
						badgeNum: 170
					},
				]
				uni.showToast({
					title: '刷新成功'
				})
				uni.stopPullDownRefresh();

			}, 1000);
		}
	}
</script>

<style lang="scss" scoped>
	.paper {
		border-top: 1rpx solid #EEEEEE;
		padding: $common-padding;
		
	}
</style>
