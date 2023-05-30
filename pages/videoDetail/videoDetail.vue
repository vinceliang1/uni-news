<template>
	<view class="video-detail-wrap">
		<view class="video-box">
			<video poster="https://cbanetcdn.cba.net.cn/u/cms/www/202211/29170051mt23.jpg"
				src="https://trainingvideo.cba.net.cn/4088cd67f9ed473da549acb67f776fb6/d8a14c839a644ea6bd27673ac66d4afa-371c25b2e755bc4e3294c034b6608e41-ld.mp4">
			</video>
		</view>
		<view class="video-title-box two-row">
			2022-2023赛季CBA联赛宣传片
		</view>
		<view class="info-box">
			<text>中国男子篮球职业联赛</text>
			<text class="time">2022-11-10</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {

		}
	}
</script>

<style scoped lang="scss">
	.video-box {
		width: 100%;

		video {
			width: 100%;
		}
	}

	.video-title-box {
		font-weight: 700;
		font-size: 40rpx;
		line-height: 60rpx;
		padding: 10rpx;
		// height: 120rpx;
	}

	.info-box {
		padding: 10rpx;
		text {
			color: #b7b7b7;
			font-size: 25rpx;
		}

		.time {
			margin-left: 20rpx;
		}
	}
</style>