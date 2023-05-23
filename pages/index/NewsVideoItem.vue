<template>
	<view class="news-video-wrap">
		<view class="title-box">
			<text>{{ row.title }}</text>
		</view>
		<view class="video-box">
			<video :poster="row.url" :src="row.videoUrl">
			</video>
		</view>
		<view class="info-box">
			<text>{{ row.author }}</text>
			<text class="time">{{ row.time }}</text>
		</view>
	</view>
</template>
<script>
	export default {
		props: {
			row: {
				type: Object,
				default: () => ({})
			}
		}
	}
</script>

<style scoped lang="scss">
	.news-video-wrap {
		border-bottom: 1rpx solid #d7d7d7;
		padding: 10rpx;

		.title-box {
			text {
				font-weight: 700;
			}
		}

		.video-box {
			width: 100%;
			height: 370rpx;
			padding: 10rpx 0;

			video {
				width: 100%;
				height: 100%;
			}

		}

		.info-box {
			text {
				color: #b7b7b7;
				font-size: 25rpx;
			}

			.time {
				margin-left: 20rpx;
			}
		}
	}
</style>