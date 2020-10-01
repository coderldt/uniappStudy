<template>
	<view class="">
		<view v-for="(item,index) in list" :key="index">
			{{item}}
		</view>
		<button type="default" @click="getAuthenRespoent">获取认证方式</button>
		<button type="default" @click="setStore">开始认证</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list: []
			}
		},
		methods: {
			getAuthenRespoent() {
				let self = this
				uni.checkIsSupportSoterAuthentication({
					success(res) {
						console.log(res);
						self.list = res.supportMode
					},
					fail(error) {
						console.log(error);
					}
				})
			},
			setStore() {
				uni.startSoterAuthentication({
					requestAuthModes: ['fingerPrint', 'facial'],
					challenge: '123456',
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
