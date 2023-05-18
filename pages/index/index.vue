<template>
	<view>
		<z-paging v-model="list" ref="paging" @query="queryList">
			<view slot="top">
				<u-tabs :list="list1"></u-tabs>
			</view>
			<view v-for="item in list" :key="item.index">
				<u-cell :title="`列表长度-${item.index}`">
					<u-avatar slot="icon" shape="square" size="35" :src="item.url"
						customStyle="margin: -3px 5px -3px 0"></u-avatar>
				</u-cell>
			</view>
		</z-paging>
	</view>



</template>

<script>
	export default {
		data() {
			return {
				list1: [{
					name: '关注',
				}, {
					name: '推荐',
				}, {
					name: '电影'
				}, {
					name: '科技'
				}, {
					name: '音乐'
				}, {
					name: '美食'
				}, {
					name: '文化'
				}, {
					name: '财经'
				}, {
					name: '手工'
				}],
				list: [],
				indexList: [],
				urls: [
					'https://cdn.uviewui.com/uview/album/1.jpg',
					'https://cdn.uviewui.com/uview/album/2.jpg',
					'https://cdn.uviewui.com/uview/album/3.jpg',
					'https://cdn.uviewui.com/uview/album/4.jpg',
					'https://cdn.uviewui.com/uview/album/5.jpg',
					'https://cdn.uviewui.com/uview/album/6.jpg',
					'https://cdn.uviewui.com/uview/album/7.jpg',
					'https://cdn.uviewui.com/uview/album/8.jpg',
					'https://cdn.uviewui.com/uview/album/9.jpg',
					'https://cdn.uviewui.com/uview/album/10.jpg',
				]
			}
		},
		methods: {
			click(item) {
				console.log('item', item);
			},
			scrolltolower() {
				this.loadmore()
			},
			loadmore() {
				for (let i = 0; i < 30; i++) {
					this.indexList.push({
						url: this.urls[uni.$u.random(0, this.urls.length - 1)]
					})
				}
			},
			queryList(pageNo, pageSize) {
				console.log(pageNo)
				console.log(pageSize)
				setTimeout(() => {
					const newArr = this.urls.map((item, index) => ({
						url: item,
						index: (pageNo - 1) * pageSize + index
					}))
					this.$refs.paging.complete(newArr)
				}, 1000)
			}
		},
		onLoad() {
			// this.loadmore()
			console.log(uni.getWindowInfo().windowHeight)
		}
	}
</script>

<style scoped lang="scss">

</style>