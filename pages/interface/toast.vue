<template>
	<view class="">
		<button type="default" @click="toast">普通提醒</button>
		<button type="default" @click="loading">loading提醒</button>
		<button type="default" @click="hide">loading隐藏</button>
		<button type="default" @click="model">model提示框</button>
		<button type="default" @click="menu">操作菜单</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				menuList: ['首页', '分析', '我的']
			}
		},
		methods: {
			toast() {
				uni.showToast({
					title: '这是一个普通的提醒',
					icon: 'loading',
					success(res) {
						console.log('成功提醒', res);
					}
				})
			},
			loading() {
				uni.showLoading({
					title: '这是一个加载的loading',
					
				})
			},
			hide() {
				uni.hideLoading()
			},
			model() {
				uni.showModal({
					title: 'modal标题',
					content: 'content内容',
					success(res) {
						console.log(res);
					}
				})
			},
			menu() {
				uni.showActionSheet({
					itemList: this.menuList,
					success(res) {
						console.log(res);
					}
				})
			}
		}
	}
</script>

<style>
</style>
