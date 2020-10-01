<script>
export default {
	globalData: {
		user: {
			name: '张三',
			pass: '123'
		}
	},
	data() {
		return {
		}
	},
	onLaunch: function() {
		console.log('App Launch 初始化');
		uni.onPageNotFound((path, query) => {
			// 路由跳转
			console.log('页面未找到', path, query);
		})
		uni.onUserCaptureScreen(() => {
			console.log('用户截屏了,但是没返回消息,我没办法');
		})
	},
	onShow: function() {
		console.log('App Show 开始');
	},
	onHide: function() {
		console.log('App Hide');
	},
	onError() {
		console.log('出错了');
	},
	onTabItemTap(e) {
		console.log(e);
	},
};
</script>

<style>
/* 解决头条小程序组件内引入字体不生效的问题 */
/* #ifdef MP-TOUTIAO */
@font-face {
	font-family: uniicons;
	src: url('/static/uni.ttf');
}
/* #endif */
</style>
