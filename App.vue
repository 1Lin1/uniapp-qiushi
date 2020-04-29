<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	/* 官方uni.css - 通用组件、模板样式库，可以当作一套ui库应用 */
	@import './common/css/uni.css';
	
	/* 引入阿里图标 */
	@import './common/css/iconfont.css';
	
	/* 引入动画库 */
	@import './common/css/animate.css';
</style>
