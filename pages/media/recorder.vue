<template>
	<view class="">
		<!-- <button @click="open">打开录音</button> -->
		<button @click="open">开始录音</button>
		<button @click="stop">结束录音</button>
		<button @click="play">播放录音</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				recorderManager: null,
				innerAudioContext: null,
				voicePath: ''
			}
		},
		onLoad() {
			this.recorderManager = uni.getRecorderManager();
			this.innerAudioContext = uni.createInnerAudioContext();
			this.innerAudioContext.autoplay = true;
			
			let self = this;
			this.recorderManager.onStop(function (res) {
				console.log('recorder stop' + JSON.stringify(res));
				self.voicePath = res.tempFilePath;
			});
			this.recorderManager.onError((error) => {
				console.log('错误', error);
				console.log('请检查是否打开录音设置');
			})
			
			this.innerAudioContext.onPlay(function(res){
				console.log(res, '播放了吗');
			})
		},
		methods: {
			open() {
				console.log('开始录入');
				this.recorderManager.start()
			},
			stop() {
				this.recorderManager.stop()
			},
			play() {
				this.innerAudioContext.src = this.voicePath
				this.innerAudioContext.play();
			}
		},
	}
</script>

<style>
</style>
