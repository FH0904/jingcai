<template>
	<view>
		<view class="tui-mtop">
			<tui-tab :tabs="tabs" :currentTab="currentTab > 5 ? 0 : currentTab" bgColor="#090c15" @change="change" itemWidth="50%" ></tui-tab>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				tabs: [
					{
						name: '全部'
					},
					{
						name: '存款'
					},
					{
						name:'提款'
					},
					{
						name:'优惠'
					}
				],
				currentTab:0,
			}
		},
		methods: {
			change(e) {
				this.currentTab = e.index;
				console.log(e);
			},
		}
	}
</script>

<style>
	.tui-tabs-view{
		top: 88rpx;
		background-color: #141c2a !important;
	}
</style>
