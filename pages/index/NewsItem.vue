<template>
	<view class="news-item-wrap">
		<template v-if="row.urls.length === 1">
			<view class="col-item-box">
				<view class="left-box">
					<view class="title-box">
						<text class="two-row">
							{{ row.title }}
						</text>
					</view>
					<view class="info-box">
						<text>{{ row.author }}</text>
						<text class="time">{{ row.time }}</text>
					</view>
				</view>
				<view class="right-box">
					<u--image v-for="item in row.urls" :key="item" :showLoading="true" :src="item" width="233rpx"
						height="233rpx" mode="aspectFill"></u--image>
				</view>
			</view>
		</template>
		<template v-if="row.urls.length > 1">
			<view class="row-item-box">
				<view class="title-box">
					<text>{{ row.title }}</text>
				</view>
				<view class="img-box">
					<view v-for="item in row.urls" :key="item">
						<u--image :showLoading="true" :src="item" width="233rpx" height="233rpx"
							mode="aspectFill"></u--image>
					</view>
				</view>
				<view class="info-box">
					<text>{{ row.author }}</text>
					<text class="time">{{ row.time }}</text>
				</view>
			</view>
		</template>
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
	padding: 10rpx;

	.col-item-box {
		display: flex;
		justify-content: space-between;

		.left-box {
			flex-grow: 1;
			min-width: 0;
			display: flex;
			flex-wrap: wrap;
			align-content: space-between;

			.title-box {
				width: 100%;
				flex-grow: 1;

				text {
					font-weight: 700;
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

		.right-box {
			flex-shrink: 0;
		}
	}

	.row-item-box {
		.title-box {
			text {
				font-weight: 700;
			}
		}

		.img-box {
			display: flex;
			justify-content: space-between;
			padding: 10rpx 0;
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



}
</style>