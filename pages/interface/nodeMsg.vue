<template>
	<view class="">
		<button type="default" @click="btnclick">获取节点信息</button>
		<button type="default" @click="savefile">选择文件</button>
		<button type="default" @click="login">登录</button>
		{{serve}}
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list: [],
				serve: null
			}
		},
		methods: {
			btnclick() {
				this.list = uni.createSelectorQuery().in(this)
				console.log(this.list);
			},
			savefile() {
				uni.chooseImage({
					success(res) {
						for(let i of res.tempFilePaths) {
							uni.saveFile({
								tempFilePath: i,
								success(res) {
									console.log(res.savedFilePath);
								}
							})
						}
						uni.saveFile({
							
						})
						console.log(res);
					}
				})
			},
			login() {
				uni.login({
					// provider: 'weixin',
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
