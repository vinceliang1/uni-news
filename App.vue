<script>
	export default {
		globalData: {
			// 状态栏高度
			statusBarHeight: 0,
			// 头部高度
			headBarHeight: 0,
			// 导航栏高度
			navBarHeight: 0
		},
		// 当uni-app 初始化完成时触发（全局只触发一次）
		onLaunch: function() {
			console.log('App Launch')

			this.globalData.statusBarHeight = uni.getSystemInfoSync().statusBarHeight

			// #ifdef MP-WEIXIN
			// 除了APP跟H5,都执行
			const custom = uni.getMenuButtonBoundingClientRect()

			this.globalData.navBarHeight = (custom.top - this.globalData.statusBarHeight) * 2 + custom.height

			this.globalData.headBarHeight = this.globalData.navBarHeight + this.globalData.statusBarHeight

			// #endif

			// #ifdef APP-PLUS || H5
			// 如果是APP跟H5，就执行
			this.globalData.navBarHeight = 80

			this.globalData.headBarHeight = this.globalData.statusBarHeight + this.globalData.navBarHeight
			// #endif


		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style lang="scss">
	/*每个页面公共css */
	@import "@/uview-ui/index.scss";
	// iconfont图标
	@import "@/static/iconfont/iconfont.css"
</style>