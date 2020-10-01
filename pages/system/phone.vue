<template>
	<view class="">
		<button type="default" @click="phone">电话</button>
		<button type="default" @click="code">扫码</button>
		<button type="default" @click="blueTooth">蓝牙</button>
		<input type="text" v-model="value"/>
		<button type="default" @click="clipboard">拷贝粘贴板set</button>
		<button type="default" @click="clipboard">拷贝粘贴板get</button>
		屏幕亮度
		<input type="text" v-model="screenlight" @input="screenheight" />
		<button type="default" @click="screenconst">保持常量</button>
		<button type="default" @click="setcontact">设置通讯录</button>
		<!-- #ifdef MP-WEIXIN -->
			<button type="default" @click="getWifiList">获取wifi列表</button>
			<button type="default" @click="getbattery">获取电量</button>
		<!-- #endif -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				value: '',
				screenlight: ''
			}
		},
		methods: {
			phone() {
				uni.makePhoneCall({
					phoneNumber: 18735674692,
					success() {
						console.log('拨打成功');
					}
				})
			},
			code() {
				uni.scanCode({
					success(res) {
						console.log(res);
					}
				})
			},
			blueTooth() {
				uni.navigateTo({
					url: './blueTooth'
				})
			},
			clipboard() {
				uni.setClipboardData({
					data: this.value,
					success(res) {
						console.log(res.data);
						uni.hideToast()
					}
				})
			},
			getWifiList() {
				// wx.
			},
			getbattery() {
				wx.getBatteryInfo({
					success(res) {
						console.log(res);
					}
				})
			},
			screenheight() {
				uni.setScreenBrightness({
					value: this.screenlight,
					success(res) {
						console.log(res);
					}
				})
			},
			screenconst() {
				uni.setKeepScreenOn({
					keepScreenOn: true
				})
			},
			setcontact() {
				uni.addPhoneContact({
					firstName: '张三',
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
