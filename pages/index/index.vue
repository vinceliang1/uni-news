<template>
	<view>
		<z-paging v-model="list" ref="paging" @query="queryList">
			<view slot="top">
				<u-tabs :list="tabOptions" :activeStyle="{
					color: '#303133',
					fontWeight: 'bold',
					transform: 'scale(1.05)'
				}" :inactiveStyle="{ color: '#606266', transform: 'scale(1)' }" @click="changeTabs"
					:current="currentTabIndex"></u-tabs>
			</view>
			<view v-for="item in list" :key="item.id">
				<template v-if="!item.videoUrl">
					<NewsItem :row="item" />
				</template>
				<template v-if="item.videoUrl">
					<NewsVideoItem :row="item" />
				</template>
			</view>
		</z-paging>
	</view>
</template>

<script>
import NewsItem from './NewsItem.vue'
import NewsVideoItem from './NewsVideoItem.vue'
export default {
	components: {
		NewsItem,
		NewsVideoItem
	},
	data() {
		return {
			tabOptions: [{
				name: '推荐',
				key: 'recommend'
			}, {
				name: '国家队',
				key: 'national'
			}, {
				name: 'CBA',
				key: 'cba'
			}, {
				name: 'WCBA',
				key: 'wcba'
			}, {
				name: 'NBL',
				key: 'nbl'
			}, {
				name: '超三',
				key: 'superThree'
			}, {
				name: 'CUBA',
				key: 'cuba'
			}, {
				name: '小篮球',
				key: 'miniBasketball'
			}, {
				name: '其他',
				key: 'other'
			}],
			currentTabIndex: 0,
			list: [],

			listArray: [{
				urls: ['https://cbanetcdn.cba.net.cn/u/cms/www/202201/041438181o5r.jpg'],
				title: 'CJBL北京赛区男子组最佳阵容出炉啦！',
				time: '2022-01-04',
				author: '中国篮协'
			},
			{
				urls: ['https://cbanetcdn.cba.net.cn/u/cms/www/202112/01092019ribe.png',
					'https://cbanetcdn.cba.net.cn/u/cms/www/202112/0109293791l6.jpg',
					'https://cbanetcdn.cba.net.cn/u/cms/www/202106/16190533s1bq.jpeg'
				],
				title: '感受信仰力量，传承红色基因！上海青年女篮参加爱国主义教育',
				time: '2021-12-01',
				author: '青年女篮'
			},
			{
				url: 'https://cbanetcdn.cba.net.cn/u/cms/www/202211/29170051mt23.jpg',
				videoUrl: 'https://trainingvideo.cba.net.cn/4088cd67f9ed473da549acb67f776fb6/d8a14c839a644ea6bd27673ac66d4afa-371c25b2e755bc4e3294c034b6608e41-ld.mp4',
				title: '2022-2023赛季CBA联赛宣传片',
				time: '2022-11-10',
				author: '中国男子篮球职业联赛'
			}

			]
		}
	},
	methods: {
		changeTabs(item) {
			console.log(item)
		},
		click(item) {
			console.log('item', item);
		},

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
		}
	},
	onLoad() {
		// this.loadmore()
		console.log(uni.getWindowInfo().windowHeight)
	}
}
</script>

<style scoped lang="scss"></style>