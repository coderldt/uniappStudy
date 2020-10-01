<template>
	<view class="">
		<button type="default" @click="getServe">获取服务商</button>
		<button type="default" @click="getLogin">登录接口</button>
		<button type="default" @click="checkLogin">检查接口</button>
		<button type="default" @click="loginDetail">获取详情</button>
		
		<button type="default" @click="switchShare">分析页面</button>
		<button type="default" @click="switchpay">支付页面</button>
	</view>
</template>

<script>
	export default {
		methods: {
			getServe() {
				uni.getProvider({
					service: 'payment',
					success(res) {
						console.log(res);
					}
				})
			},
			getLogin() {
				uni.login({
					success(res) {
						console.log('成功', res);
					},
					fail(error) {
						console.log('失败', error);
					}
				})
			},
			checkLogin() {
				uni.checkSession({
					success(res) {
						console.log('成功检查', res);
					}
				})
			},
			loginDetail() {
				uni.getUserInfo({
					lang: 'zh_CN',
					success(res) {
						console.log(res);
					}
				})
			},
			switchShare() {
				uni.navigateTo({
					url: './share'
				})
			},
			switchpay() {
				uni.navigateTo({
					url: './pay'
				})
			}
		}
	}
</script>

<style>
</style>
