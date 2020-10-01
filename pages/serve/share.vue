<template>
	<view class="">
		<button type="default" @click="share">分享文字</button>
	</view>
</template>

<script>
	export default {
		methods: {
			share() {
				uni.share({
				    provider: "weixin",
				    scene: "WXSceneSession",
				    type: 1,
				    summary: "我正在使用HBuilderX开发uni-app，赶紧跟我一起来体验！",
				    success: function (res) {
				        console.log("success:" + JSON.stringify(res));
				    },
				    fail: function (err) {
				        console.log("fail:" + JSON.stringify(err));
				    }
				});
			}
		}
	}
</script>

<style>
</style>
