<template>
	<view class="system">
		<button type="default" @click="getSystemInfo">获取基本设备信息</button>
		<button type="default">监听内存警告</button>
		<button type="default" @click="getNetwork">获取网络信息</button>
	</view>
</template>

<script>
	export default {
		methods: {
			getSystemInfo() {
				uni.getSystemInfo({
					success(res) {
						console.log(res);
					}
				})
			},
			getNetwork() {
				uni.getNetworkType({
					success(res) {
						console.log(res);
					}
				})
			}
		},
		onLoad() {
			uni.onMemoryWarning(res => {
				console.log('内存不足警告', res);
			})
			uni.onUIStyleChange((res) => {
				console.log('123', res);
			})
		}
	}
</script>

<style>
</style>
