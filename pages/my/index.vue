<template>
	<view class="my">
		<text>我的测试页面</text>
		<text>我的位置: {{pos}}</text>
		<button type="default" @click="submit">登录</button>
		<button type="default" @click="checkLogin">检查登录</button>
		<button type="default" @click="getLocaltion">获取位置权限</button>
		<button type="default" @click="setLocaltion">设置位置</button>
		<button type="default" @click="watchLocaltion">查看位置</button>
		<button type="default" @click="">打开相机</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				pos: ''
			}
		},
		methods: {
			submit() {
				uni.setStorage({
					key: 'user',
					data: { username: '张三', password: '18712345678' }
				})	
				// uni.setStorage('user', { username: '张三', password: '18712345678' })	
			},
			async checkLogin() {
				const data = await uni.getStorage({
					key: "user"
				})
					console.log(data);
				if(data[1].data) {
					console.log(data);
				}else {
					console.log('没有登录');
				}
			},
			getLocaltion() {
				uni.getLocation({
					success(res) {
						console.log(res);
					}
				})
			},
			setLocaltion() {
				const that = this
				uni.chooseLocation({
					success(res) {
						that.pos = res.address
					}
				})
			},
			watchLocaltion() {
				uni.getLocation({
					success(res) {
						uni.openLocation({
							longitude: res.longitude,
							latitude: res.latitude,
						})
					},
					fail() {
						console.log('请先授权');
					}
				})
			},
			openImages() {
				uni.chooseImage({
					count: 1,
					success(res) {
						console.log(res);
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
