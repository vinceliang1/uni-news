<template>
	<view class="newx-item-wrap">
		<view class="title-box">
			title
		</view>
		<view class="img-wrap">
			<view class="img-item">
				<u--image :showLoading="true" src="https://cbanetcdn.cba.net.cn/u/cms/www/202112/01092019ribe.png"
					width="233rpx" height="233rpx" mode="aspectFill"></u--image>
			</view>
			<view class="img-item img-item-padding">
				<u--image :showLoading="true" src="https://cbanetcdn.cba.net.cn/u/cms/www/202112/0109293791l6.jpg"
					width="233rpx" height="233rpx"></u--image>
			</view>
			<view class="img-item">
				<u--image :showLoading="true" src="https://cbanetcdn.cba.net.cn/u/cms/www/202106/16190533s1bq.jpeg"
					width="233rpx" height="233rpx"></u--image>
			</view>
		</view>
	</view>
</template>

<script>
</script>

<style scoped lang="scss">
	.img-wrap {
		display: flex;
		justify-content: space-between;
		padding: 10rpx;

		.img-item-padding {
			// padding: 0 15rpx;
		}
	}
</style>