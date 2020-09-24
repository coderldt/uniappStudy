<template>
	<view class="container">
		<view class="intro">本项目已包含uni ui组件，无需import和注册，可直接使用。在代码区键入字母u，即可通过代码助手列出所有可用组件。光标置于组件名称处按F1，即可查看组件文档。</view>
		<view class="detail">本项目已包含uni ui组件，无需import和注册，可直接使用。在代码区键入字母u，即可通过代码助手列出所有可用组件。光标置于组件名称处按F1，即可查看组件文档。</view>
		<view class="lg">本项目已包含uni ui组件，无需import和注册，可直接使用。在代码区键入字母u，即可通过代码助手列出所有可用组件。光标置于组件名称处按F1，即可查看组件文档。</view>
		<uni-link :href="href" :text="href"></uni-link>
		<text>{{name}}</text>
		<button type="default" @click="navigateTo">关注</button>
		<button type="default" @click="redirectTo">发布</button>
		<button type="default" @click="tabbar">我的</button>
		<button type="default" @click="emit">初始化事件</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				href: 'https://uniapp.dcloud.io/component/README?id=uniui',
				name: ''
			}
		},
		created() {
			console.log('组件created初始化');
		},
		mounted() {
			console.log('组件mounted初始化');
		},
		methods: {
			navigateTo() {
				// console.log(this.route);
				uni.navigateTo({
					url: '../home/switch?id=123456789',
					events: {
						// 监听跳转页面返回的信息
						// acceptDataFromOpenedPage(data) {
						// 	console.log('监听器', data);
						// }
					},
					success(res) {
						// 向跳转的页面发送新的事件
						// res.eventChannel.emit('acceptDataFromOpenerPage', { ret: '返回的数据' })
					}
				})
			},
			redirectTo() {
				uni.redirectTo({
					url: "../home/redirectTo?name=张三",
					events: {
						callback(data) {
							console.log(data);
						}
					},
					success(res) {
						console.log(res);
					}
				})
			},
			tabbar() {
				uni.switchTab({
					url: '../my/index',
					success(res) {
						console.log(res);
					}
				})
			},
			emit() {
				uni.$emit('init', { msg: '初始化' })
			}
		},
		onShow() {
			console.log(uni.getSystemInfoSync().system);
			// console.log(getApp().globalData);
			getApp().globalData.user.name = '李四'
			this.name = getApp().globalData.user.name
			console.log('组件内部onshow');
		},
		onAddToFavorites() {
			console.log('我收藏了');
			if(process.env.NODE_ENV == 'development') {
				console.log('我在测试开发环境');
			}else {
				console.log('我在测试生产环境');
			}
			
		},
		onPageScroll(scrollTop) {
			console.log(screenTop);
		}
	}
</script>

<style lang="scss">
	.container {
		padding: 20px;
		font-size: 14px;
		line-height: 24px;
		
		
		.intro {
			font-size: $uni-font-size-sm;
		}
		
		.detail {
			font-size: $uni-font-size-base;
		}
		
		.lg {
			font-size:$uni-font-size-lg;
		}
	}
</style>
