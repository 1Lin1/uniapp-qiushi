<template>
	<view class="indexContent">
		
		<tab-bar :tabBars="tabBars"></tab-bar>
		<block v-for="(item,index) in list" :key="item.id">
			<indexlist :item="item"></indexlist>
		</block>
	</view>
</template>

<script>
	import indexlist from '../../components/index/index-list.vue'
	import tabBar from '../../components/index/tabBar.vue'
	export default {
		data() {
			return {
				
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
							cNum:2,//0:不操作 1:顶 2::踩
							dingNum:11,
							caiNum:5
						},
						commentNum:10,
						shareNum:11
					},
				]
			}
		},
		onLoad() {

		},
		components:{
			indexlist,
			tabBar
		},
		methods: {
			clickTap(){
				console.log('触发')
			}
		}
	}
</script>

<style lang="scss" scoped>
	.indexContent{
		margin-top: 100upx;
	}
	
	
	// .content:nth-of-type(1){
	// 	margin-top: 88upx;
	// }
	
</style>
