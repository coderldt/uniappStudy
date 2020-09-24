<template>
	<view class="view">
		{{content}}
		
		<button type="default" @click="redirectTo">发布</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				content: '123'
			}
		},
		mounted() {
			// this.content = this.$route.query
		},
		methods: {
			redirectTo() {
				uni.navigateTo({
					url: "../my/star",
					success() {
						console.log(getCurrentPages());
					}
				})
			}
		},
		onLoad(option) {
			// console.log('跳转过来啊曹', option);
			// this.content = option.id
			const eventChannel = this.getOpenerEventChannel()
			
			// eventChannel.emit('acceptDataFromOpenedPage', { callbackTest: '123' })
			// eventChannel.on('acceptDataFromOpenerPage', (data) => {
			// 	console.log('又传回来的值', data);
			// })
		},
		
	}
</script>

<style>
</style>
