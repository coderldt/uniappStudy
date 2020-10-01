<template>
	<view class="">
		<button type="default" @click="inittooth">初始化蓝牙(不支持mac外的手机)</button>
	</view>
</template>

<script>
	export default {
		methods: {
			inittooth() {
				uni.openBluetoothAdapter({
					success(res) {
						console.log(res, '初始化成功');
					},
					fail(error) {
						console.log(error);
					}
				})
			}
		}
	}
</script>

<style>
</style>
