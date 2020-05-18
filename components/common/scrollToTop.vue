<template>
  <view class="back-top">
    <image src="../../static/common/top.png" mode="widthFix"></image>
  </view>
</template>

<script>
  export default {
    name: "BackTop"
  }
</script>

<style scoped lang="scss">

  .back-top{
    position: fixed;
	z-index: 999;
    right: 10px;
    bottom: 60px;
	
	image{
		width: 80rpx;
		height: 80rpx;
	}
  }

 
</style>
