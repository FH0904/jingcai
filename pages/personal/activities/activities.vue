<template>
	<view>
		<view class="tui-mtop">
			<tui-tab :tabs="tabs" :currentTab="currentTab > 3 ? 0 : currentTab" bgColor="#090c15" @change="change" itemWidth="50%" ></tui-tab>
		</view>
		<swiper :current="currentTab" :duration="300" @change="swiperChange" :style="'height:'+ scrollH + 'px'">
			<swiper-item>
				<view class="swiper-item">
					<scroll-view scroll-y="true" :style="'height:' + scrollH + 'px;'">
						<view class="promotion-list">
							<view class="promotion-card">
								<view class="card-header">
									<image src="../../../static/images/icon33.jpg" mode="" class="card-header-img"></image>
									<view class="card-title">
										首存50送18
									</view>
									<view class="card-time">
										2018-10-18 00:00:00
									</view>
								</view>
							</view>
						</view>
					</scroll-view>
				</view>
			</swiper-item>
			<swiper-item>
				<view class="swiper-item">
					<scroll-view scroll-y="true" :style="'height:' + scrollH + 'px;'">
						<view class="task-list">
							<view class="task-type-list">
								<view class="type-title">
									注册有礼
								</view>
								<view class="task-item">
									<view class="task-info">
										<view class="task-title">
											<text>注册送10</text>
											<text class="task-target"></text>
										</view>
										<view class="task-detail">
											注册时间：2018年9.28号起
										</view>
									</view>
									<view class="task-btn">
										未完成
									</view>
								</view>
							</view>
						</view>
					</scroll-view>
				</view>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				currentTab:0,
				tabs: [
					{
						name: '优惠'
					},
					{
						name: '任务'
					}
				],
				scrollH:500
			}
		},
		methods: {
			change(e) {
				this.currentTab = e.index;
				console.log(e);
			},
			swiperChange(data){
				this.currentTab = data.detail.current;
			}
		},
		onLoad() {
			uni.getSystemInfo({
				success: res => {
					this.scrollH = res.windowHeight - uni.upx2px(86)
				}
			})
		}
	}
</script>

<style lang="less">
	.tui-tabs-view{
		top: 88rpx;
		background-color: #141c2a !important;
	}
	swiper{
		margin-top: 86rpx;
	}
	.promotion-list{
		padding-left: 16rpx;
		padding-right: 16rpx;
		.promotion-card{
			width: 100%;
			background-color: #151b29;
			border-radius: 8rpx;
			margin-top: 16rpx;
			margin-bottom: 16rpx;
			.card-header{
				text-align: left;
				padding-bottom: 12rpx;
				.card-header-img{
					border-radius: 8rpx 8rpx 0 0;
					height: 208rpx;
				}
				.card-title{
					padding-top: 28rpx;
					margin-left: 8rpx;
					margin-left: 32rpx;
				}
				.card-time{
					margin-left: 32rpx;
					font-size: 12rpx;
				}
			}
		}
	}
	.task-list{
		padding: 0 16rpx;
		box-sizing: border-box;
		.task-type-list{
			text-align: left;
			.type-title{
				margin-top: 32rpx;
				padding: 0 0 14rpx 32rpx;
				font-size: 24rpx;
				color: #758bb5;
				border-bottom: 1px solid #182031;
			}
			.task-item{
				margin-top: 8rpx;
				background: #151b29;
				border-radius: 8rpx;
				padding: 32rpx;
				display: flex;
				justify-content: space-between;
				align-items: center;
				.task-info{
					display: flex;
					flex-direction: column;
					flex: 1;
					padding-right: 64rpx;
					.task-title{
						font-size: 28rpx;
						color: #BACEF1;
						.task-target{
							color: #526585;
						}
					}
					.task-detail{
						font-size: 24rpx;
						color: #758bb5;
						margin-top: 22rpx;
					}
				}
				.task-btn{
					width: 156rpx;
					height: 60rpx;
					line-height: 60rpx;
					text-align: center;
					background-image: linear-gradient(90deg,#244053,#253c53);
					color: #5e7a96;
					font-size: 24rpx;
					border-radius: 8rpx;
				}
			}
		}
	}
</style>
