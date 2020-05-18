<template>
	<view>
		<!-- 自定义导航栏 -->
		<uni-nav-bar 
		:statusBar="true" 
		leftIcon="back" 
		@clickLeft="back"
		@clickRight="submit"
		rightText="发布"
		>
		
		<view class="center u-f-ajc" @tap="changeLook">
			{{changeLookText}}
			<view class="icon iconfont icon-xialazhankai"></view>
		</view>
		
		</uni-nav-bar>
		
		<!-- 输入框 -->
		<view class="uni-textarea">
			<textarea  v-model="text" placeholder="请输入内容吧~" maxlength="500"  />
		</view>
		
		
		<!-- 上传图片 -->
		<upload-img @getImageList="getImageList"></upload-img>
		
		<!-- 弹出层 公告 -->
		<uni-popup ref="popup">
			<view class="popup " >
				<view class="topImage u-f-ajc">
					<image src="../../static/common/gonggao.png" mode="aspectFit"></image>
				</view>
				<view class="center-content">
					<view>1.黄色，政治及影响身心健康的内容</view>
					<view>2.黄色，政治及影响身心健康的内容</view>
					<view>3.黄色，政治及影响身心健康的内容</view>
					<view>4.黄色，政治及影响身心健康的内容</view>
				</view>
				<view class="popup-Button u-f-ajs">
					<button  @tap="closePopup">朕知道了</button>
				</view>
			</view>
			
		</uni-popup>
		
	</view>
</template>

<script>
	let changeLook = ['所有人可见','仅自己可见']
	
	import uniNavBar from '../../components/uni-nav-bar/uni-nav-bar.vue';
	import uploadImg from '../../components/common/upload-img.vue';
	import uniPopup from '../../components/uni-popup/uni-popup.vue'
	export default {
		components:{
			uniNavBar,
			uploadImg,
			uniPopup
		},
		data() {
			return {
				changeLookText:'所有人可见',
				text:'',
				imageList:[],
				isShowPopup:true,  //是否立即显示
				isget:false, //用户是否点击保存组
			};
		},
		onLoad() {
			uni.getStorage({
			    key: 'caogao_text',
			    success:res => {
			        this.text = res.data;
			    }
			});
		},
		// 返回按钮监听
		onBackPress() {
			// 判断内容是否为空
			if(this.text == '' && this.imageList.length < 1) return;
			if(!this.isget){
				this.baocun();
				return true;
			}
		},
		methods:{
			
			// 是否保存草稿操作
			baocun(){
				uni.showModal({
					content: '是否要保存为草稿？',
					cancelText: '不保存',
					confirmText: '保存',
					success: res => {
						// 确定
						if(res.confirm){
							uni.setStorage({
							    key: 'caogao_text',
							    data: this.text,
							    success: res => {
							        console.log('success');
							    }
							});
						} else if (res.cancel) {
							console.log('用户点击取消');
							uni.setStorage({
							    key: 'caogao_text',
							    data: '',
							    success: res => {
							        console.log('success');
							    }
							});
						}
						this.isget=true;
						uni.navigateBack({
							delta: 1
						});
					},
				});
			},
			// 返回监听
			back(){
				uni.navigateBack({
					delta:1
				})
			},
			
			// 发布
			submit(){
				console.log('发布')
			},
			
			// 获取上传的图片
			getImageList(imageList){
				this.imageList = imageList;
			},
			
			// 隐私设置
			changeLook(){
				uni.showActionSheet({
					itemList:changeLook,
					success:(res) => {
						this.changeLookText = changeLook[res.tapIndex]
					},
					fail:(err) => {
						console.log(err)
					}
				})
			},
			
			// 关闭弹出层
			closePopup(){
				  this.$refs.popup.close()
			}
			
		},
		
	}
</script>

<style lang="scss" scoped>
	.center{
		width: 400rpx;
	}
	
	.uni-textarea{
		border-bottom: 1rpx solid #EEEEEE;
	}
	
	
	// 弹出窗口
	.popup{
		width: 600rpx;
		height: 900rpx;
		background-color: #FFFFFF;
		font-weight: bold;
		.topImage{
			image{
				width: 50%;
			}
		}
		.center-content{
			text-align: center;
		}
		.popup-Button{
			height: 20%;
			button{
				width: 480rpx;
				background-color: #FEE42A;
			}
			
		}
	}
	
	
	
	
</style>
