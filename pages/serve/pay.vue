<template>
	<view class="">
		<button type="default" @click="pay">支付</button>
		<button type="default" @click="author">获取权限</button>
		<button type="default" @click="set">吊起设置页面</button>
		<button type="default" @click="chooseaddress">收获地址</button>
		<button type="default" @click="title">获取发票</button>
		<button type="default" @click="getuniappmsg">获取小程序信息</button>
		<button type="default" @click="runData">计步器</button>
		<button type="default" @click="opencard">卡券</button>
		<button type="default" @click="addtemplate">添加模板消息</button>
		<button type="default" @click="three">第三方平台数据</button>
	</view>
</template>

<script>
	export default {
		methods: {
			pay() {
				// 自己看参数
				// uni.requestPayment({
				// 	provider: 'wxpay',
				// 	orderInfo: '123456',
				// 	timeStamp: 
				// })
			},
			author() {
				uni.authorize({
				    scope: 'scope.userLocation',
				    success() {
				        uni.getLocation()
				    }
				})
			},
			set() {
				uni.openSetting({
					success(res) {
						console.log(res);
					}
				})
			},
			chooseaddress() {
				uni.chooseAddress({
					success(res) {
						console.log(res);
					}
				})
			},
			title() {
				uni.chooseInvoiceTitle({
					success(res) {
						console.log(res);
					}
				})
			},
			getuniappmsg() {
				let msg = uni.getAccountInfoSync()
				console.log(msg);
			},
			runData() {
				wx.getWeRunData({
					success(res) {
						console.log(res);
					},
					fail(error) {
						console.log(error);
					}
				})
			},
			opencard() {
				uni.openCard({
					cardList: [
						{
							cardId: '',
							code: ''
						}
					],
					success(res) {
						console.log(res);
					},
					fail(error) {
						console.log(error);
					}
				})
			},
			addtemplate() {
				uni.addtemplate({
					access_token: ''
				})
			},
			three() {
				uni.getExtConfig({
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
