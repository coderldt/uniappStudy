<template>
	<view class="hidden_header">
		<view class="status_bar">
		</view>
		<button type="default" @click="switchRecdrder">录音器</button>
		<button type="default" @click="switchVideo">视频器</button>
		<view class="body" :style="{height: height}">
			<block v-for="(item, index) in 10" :key="index">
				{{item}}
			</block>
			<button type="default" @click="accept">接受事件</button>
			<text class="content">{{content}}</text>
			<!-- #ifdef MP-WEIXIN -->
				微信小程序的内容
			<!-- #endif -->
			<!-- #ifdef H5 -->
				h5的内容
			<!-- #endif -->
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				height: '',
				list: [
					{ title: '第一个' },
					{ title: '第二个' },
					{ title: '第三个' },
					{ title: '第四个' },
					{ title: '第五个' },
				],
				content: '待覆盖数据'
			}
		},
		mounted() {
		},
		methods: {
			switchRecdrder() {
				uni.navigateTo({
					url: "../media/recorder"
				})
			},
			switchVideo() {
				uni.navigateTo({
					url: "../media/video"
				})
			}
		},
		onLoad(e) {
			console.log(Page.data);
			this.height = uni.getSystemInfoSync().statusBarHeight + 'rpx'
			// console.log(uni.getSystemInfoSync());
			
			uni.$on('init', (data) => {
				this.content = data.msg
				console.log(data);
			})
		},
		onShow() {
			console.log('组件内部onshow');
		},
		onPageScroll(e) {
			console.log(e);
		}
	}
</script>

<style>
	.status_bar {
		bottom: calc(var(--window-bottom) + 10px);
		height: var(--status-bar-height);
	}
</style>
