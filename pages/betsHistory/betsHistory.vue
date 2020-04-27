<template>
	<view class="betsHistory">
		<view class="tui-mtop">
			<tui-tab :tabs="tabs" :currentTab="currentTab > 3 ? 0 : currentTab" bgColor="#090c15" @change="change" itemWidth="50%" ></tui-tab>
		</view>
		<swiper style="height: 600rpx;" :current="currentTab" @change='swiperChange'>
			<swiper-item>
				<view class="swiper-item">
					<view class="empty-note">
						好久不见，去赢点钱玩玩吧...
					</view>
					<view class="btn">
						<view class="button-border">
							<view class="button-content">
								去赢两个
							</view>
						</view>
					</view>
				</view>
			</swiper-item>
			<swiper-item>
				<view class="swiper-item">
					
				</view>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				tabs: [
					{
						name: '未结算'
					},
					{
						name: '已结算'
					}
				],
				currentTab:0,
			}
		},
		methods:{
			change(e) {
				this.currentTab = e.index;
				console.log(e);
			},
			// 滑动切换
			swiperChange(data) {
			  this.currentTab = data.detail.current
			},
		}
	}
</script>

<style lang="less">
	.tui-tabs-view{
		top: 88rpx;
		background-color: #141c2a !important;
	}
	.empty-note{
		margin-top: 220rpx;
		margin-bottom: 128rpx;
		color: #1ad2fe;
	}
	.btn{
		margin: 0 auto;
		width: calc(100% - 432rpx);
		margin-left: 216rpx;
		background-image: linear-gradient(90deg,#298a97,#317699);
		box-shadow: 0 0 8rpx 0 rgba(14,20,34,.5);
		height: 80rpx;
		border-radius: 8rpx;
		background: linear-gradient(90deg,#1efffa,#34cdff);
		box-shadow: 0 0 8rpx 0 rgba(14,20,34,.5);
		display: flex;
		justify-content: center;
		align-items: center;
		.button-border{
			background-image: linear-gradient(#323e57,#1d2639);
			width: calc(100% - 4rpx);
			display: flex;
			justify-content: center;
			align-items: center;
			height: 76rpx;
			border-radius: 6rpx;
			.button-content{
				background: #252f44;
				font-size: 28rpx;
				height: 72rpx;
				border-radius: 4rpx;
				border: none;
				color: #fff;
				width: calc(100% - 4rpx);
				display: flex;
				justify-content: center;
				align-items: center;
			}
		}
	}
</style>
