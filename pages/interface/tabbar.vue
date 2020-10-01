<template>
	<view class="tabbar">
		<input type="text" v-model="index" />
		<button type="default" @click="setItem">设置item</button>
		<button type="default" @click="setBack">设置背景</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				index: 0
			}
		},
		methods: {
			setItem() {
				uni.setTabBarItem({
					index: this.index,
					text: '新增的'
				})
			},
			setBack() {
				let self = this
				uni.setBackgroundColor({
					backgroundColor: self.index,
					success(res) {
						console.log(self.index, typeof self.index);
						console.log(res);
					},
					error(error) {
						console.log(error);
					}
				})
			}
		}
	}
</script>

<style>
</style>
