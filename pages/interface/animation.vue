<template>
	<view class="">
		<view class="" :animation="animationData" style="width: 200px; height: 200px; background-color: #007AFF;">
			
		</view>
		<button type="default" @click="ani1">先旋转后放大</button>
		<button type="default" @click="scroll">滚动0</button>
		<view v-for="(item,index) in scrollList" :key="index">
			<view :style="{'background-color': `#${item}`, width: '200px', height: '200px'}">
				
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				animationData: null,
				scrollList: ['f00', '0f0', '00f', 'ff1249', '15f996', 'f43f46']
			}
		},
		onLoad() {
			this.animation = uni.createAnimation({
				delay: 1000,
				timingFunction: 'ease-in-out',
				duration: 2000
			})
			
			this.animation.scale(2,2).rotate(45).step()
			
			this.animationData = this.animation.export()
		},
		methods: {
			ani1() {
				console.log(this.animation);
				this.animation.rotate(75).step()
				this.animation.scale(2).step()
				this.animationData = this.animation.export()
			},
			scroll() {
				uni.pageScrollTo({
					scrollTop: 0,
					duration: 1000
				})
			}
		},
		onPullDownRefresh() {
			console.log('下拉刷新', );
		}
	}
</script>

<style>
</style>
