<template>
	<view>
		<z-paging v-model="list" ref="paging" @query="queryList">
			<view v-for="item in list" :key="item.id" class="video-item">
				<view class="video-box">
					<view class="video-title-box">
						<text class="video-title two-row">2022-2023赛季CBA联赛宣传片</text>
					</view>
					<u--image :showLoading="true" src="https://cbanetcdn.cba.net.cn/u/cms/www/202112/01092019ribe.png"
						width="100%" height="370rpx" mode="aspectFill"></u--image>
					<view class="play-btn-box" @click="goVideoDetail">
						<!-- <u-icon name="play-right" color="#fff" size="40rpx"></u-icon> -->
						<text class="iconfont icon-bofang"></text>
					</view>
				</view>
				<view class="info-box">
					<view class="left">
						<text>青年女篮</text>
						<text class="time">2021-12-01</text>
					</view>
					<view class="right">
						<u-icon :name="!item.attention ? 'heart' : 'heart-fill'"
							:color="!item.attention ? '#d7d7d7' : '#DFC70C'" size="60rpx"
							@click="changeAttention(item)"></u-icon>
					</view>
				</view>
			</view>
		</z-paging>
	</view>
</template>

<script>
	export default {
		components: {},
		data() {
			return {
				list: [],
				listArray: [{
						urls: ['https://cbanetcdn.cba.net.cn/u/cms/www/202201/041438181o5r.jpg'],
						title: 'CJBL北京赛区男子组最佳阵容出炉啦！',
						time: '2022-01-04',
						author: '中国篮协',
						attention: false
					},
					{
						urls: ['https://cbanetcdn.cba.net.cn/u/cms/www/202112/01092019ribe.png',
							'https://cbanetcdn.cba.net.cn/u/cms/www/202112/0109293791l6.jpg',
							'https://cbanetcdn.cba.net.cn/u/cms/www/202106/16190533s1bq.jpeg'
						],
						title: '感受信仰力量，传承红色基因！上海青年女篮参加爱国主义教育',
						time: '2021-12-01',
						author: '青年女篮',
						attention: false
					},
					{
						url: 'https://cbanetcdn.cba.net.cn/u/cms/www/202211/29170051mt23.jpg',
						videoUrl: 'https://trainingvideo.cba.net.cn/4088cd67f9ed473da549acb67f776fb6/d8a14c839a644ea6bd27673ac66d4afa-371c25b2e755bc4e3294c034b6608e41-ld.mp4',
						title: '2022-2023赛季CBA联赛宣传片',
						time: '2022-11-10',
						author: '中国男子篮球职业联赛',
						attention: false
					}

				]
			}
		},
		methods: {
			queryList(pageNo, pageSize) {
				console.log(pageNo)
				console.log(pageSize)
				setTimeout(() => {
						// 这里模拟从后端获取到数据
						const res = [...Array(20).keys()].map(index => {
							return {
								id: `${Math.floor(Math.random() * 9999999999)}`,
								...this.listArray[index % 3],
							}
						});
						console.log(res);

						// const newArr = this.urls.map((item, index) => ({
						// 	url: item,
						// 	index: (pageNo - 1) * pageSize + index
						// }))
						this.$refs.paging.complete(res)
					},
					1000)
			},
			changeAttention(item) {
				console.log('------------------------')
				item.attention = !item.attention
			},
			goVideoDetail() {
				uni.navigateTo({
					url: '/pages/videoDetail/videoDetail',
					animationType: 'slide-in-right',
					animationDuration: 700
				})
			}
		}
	}
</script>

<style scoped lang="scss">
	.video-item {
		padding: 10rpx;
		border-bottom: 1rpx solid #d7d7d7;

		.video-box {
			position: relative;
			width: 730rpx;
			padding-bottom: 10rpx;

			.video-title-box {
				position: absolute;
				top: 0;
				left: 0;
				width: 100%;
				z-index: 1;
				color: #fff;
				// background: rgba($color: #000000, $alpha: 0.7);
				padding: 10rpx;
				box-sizing: border-box;

				.video-title {
					font-weight: 700;
				}
			}

			.play-btn-box {
				position: absolute;
				left: 50%;
				top: 50%;
				background: rgba($color: #000000, $alpha: .6);
				width: 76rpx;
				height: 76rpx;
				display: flex;
				justify-content: center;
				align-items: center;
				margin-left: -38rpx;
				margin-top: -38rpx;
				border-radius: 50%;

				text {
					color: #fff;
					font-size: 40rpx;
					margin-left: 10rpx;
				}
			}
		}

		.info-box {
			display: flex;
			justify-content: space-between;
			align-items: center;

			.left {
				text {
					color: #b7b7b7;
				}

				.time {
					margin-left: 20rpx;
				}
			}
		}
	}
</style>