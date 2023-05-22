<template>
	<view class="news-item-wrap">
		<!-- 	<view class="title-box">
			{{row.title}}
		</view> -->
		<view class="title-box">
			<text>{{row.title}}</text>
		</view>
		<view class="img-box">
			<view class="img-item">
				<u--image :showLoading="true" src="https://cbanetcdn.cba.net.cn/u/cms/www/202112/01092019ribe.png"
					width="233rpx" height="233rpx" mode="aspectFill"></u--image>
			</view>
			<view class="img-item">
				<u--image :showLoading="true" src="https://cbanetcdn.cba.net.cn/u/cms/www/202112/0109293791l6.jpg"
					width="233rpx" height="233rpx"></u--image>
			</view>
			<view class="img-item">
				<u--image :showLoading="true" src="https://cbanetcdn.cba.net.cn/u/cms/www/202106/16190533s1bq.jpeg"
					width="233rpx" height="233rpx"></u--image>
			</view>
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
	.news-item-wrap {
		border-bottom: 1rpx solid #d7d7d7;
		padding: 30rpx 10rpx;

		.title-box {

			text {
				font-weight: 700;
			}
		}

		.img-box {
			display: flex;
			justify-content: space-between;
			padding: 30rpx 0;
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