<template>
	<view class="">
		<button type="default" @click="open">打开video</button>
		<video :src="src" controls></video>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				src: ''
			}
		},
		methods: {
			open() {
				let self = this
				uni.chooseVideo({
					success(res) {
						console.log(res);
						self.src = res.tempFilePath
					}
				})
			}
		}
	}
</script>

<style>
</style>
