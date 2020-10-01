<template>
	<view class="">
		<button type="default" @click="toast">提醒</button>
		<button type="default" @click="nav">导航</button>
		<button type="default" @click="tabbar">tabbar</button>
		<button type="default" @click="animation">animation</button>
		<button type="default" @click="nodeMsg">节点信息</button>
	</view>
</template>

<script>
	export default {
		methods: {
			toast() {
				uni.navigateTo({
					url: './toast'
				})
			},
			nav() {
				uni.navigateTo({
					url: './nav'
				})
			},
			tabbar() {
				uni.navigateTo({
					url: './tabbar'
				})
			},
			animation() {
				uni.navigateTo({
					url: './animation'
				})
			},
			nodeMsg() {
				uni.navigateTo({
					url: './nodeMsg'
				})
			},
			
		}
	}
</script>

<style>
</style>
