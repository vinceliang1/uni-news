<template>
	<view class="top-wrap" :style="{ width:'100%',  paddingTop:`${statusBarHeight}px` }">
		<!-- #ifdef APP-PLUS || H5 -->
		<view class="nav-wrap" :style="{ width:'100%', height:`${navBarHeight}rpx` }">
			{{ title }}
		</view>
		<!-- #endif -->
		<!-- #ifdef MP-WEIXIN -->
		<view class="nav-wrap" :style="{ width:'100%', height:`${navBarHeight}px` }">
			{{ title }}
		</view>
		<!-- #endif -->
	</view>

</template>

<script>
	export default {
		props: {
			title: {
				type: String,
				default: '爱微闻'
			}
		},
		data() {
			return {
				// app: getApp()
			}
		},
		methods: {

		},
		onLoad() {},
		computed: {
			// headBarHeight: () => getApp().globalData.headBarHeight,
			statusBarHeight: () => getApp().globalData.statusBarHeight,
			navBarHeight: () => getApp().globalData.navBarHeight
		}
	}
</script>

<style scoped lang="scss">
	.top-wrap {
		background: #CC0001;
	}

	.nav-wrap {
		display: flex;
		justify-content: center;
		align-items: center;
		color: #fff;
	}
</style>