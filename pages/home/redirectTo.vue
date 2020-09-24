<template>
	<view class="content">
		<view class="">
			{{msg}}
		</view>
		<view class="">
			{{name}}
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				msg: 'redirecTo页面',
				name: 'none'
			}
		},
		onLoad() {
			
		},
		onLoad(options) {
			this.name = options.name
			const eventChangel = this.getOpenerEventChannel()
			eventChangel.emit('callback', { switchSuccess: '跳转成功啦' })
			// console.log();
		}
		
	}
</script>

<style>
</style>
