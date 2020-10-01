<template>
	<view class="nav">
		<button type="default" @click="setNav">设置导航条</button>
		<button type="default" @click="loadProgress">导航加载进度条</button>
		<button type="default" @click="hideProgress">隐藏加载进度条</button>
	</view>
</template>

<script>
	export default {
		methods: {
			setNav() {
				uni.setNavigationBarTitle({
					title: '新设置的title',
					success() {
						uni.showToast({
							title: '设置成功'
						})
					}
				})
			},
			loadProgress() {
				uni.showNavigationBarLoading()
			},
			hideProgress() {
				uni.hideNavigationBarLoading()
			}
		},
		onShow() {
			uni.setNavigationBarTitle({
				title: '新设置的title',
				success() {
					uni.showToast({
						title: '设置成功'
					})
				}
			})
		}
	}
</script>

<style>
</style>
