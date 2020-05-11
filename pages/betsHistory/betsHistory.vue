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
					<view class="order-list">
						<view class="order-card">
							<view class="odds-detail">
								<view class="odds-detail-header">
									<image src="../../static/images/icon6.svg" mode=""></image>
									<view class="title">
										获胜者 Reverse Heaven
									</view>
									<view class="type">
										第一局 赛前
									</view>
									<view class="flag-icon">
										<text>输</text>
									</view>
								</view>
								<view class="odds-detail-list">
									<view>Reverse Heaven - VS - LGD.int</view>
									<view style="height: 8rpx;"></view>
									<view>开始时间: 2020-04-13 15:00:00</view>
									<view style="height: 8rpx;"></view>
									<view>赔率: 3.61</view>
									<view style="height: 8rpx;"></view>
								</view>
							</view>
							<view class="order-info">
								<view class="order-info-row">
									<view class="order-title">
										单注
									</view>
									<view class="order-status CLOSE">
										已结算
									</view>
								</view>
								<view style="height: 12rpx;"></view>
								<view class="order-info-row">
									<view class="order-info-row-lebal">投注金额:
									<text class="total-stake">10</text>
									</view>
									<view class="order-info-row-lebal">盈利
										<text class="bonus-lose">0.00</text>
									</view>
								</view>
								<view style="height: 36rpx;"></view>
								<view class="order-info-row">
									<view>
										订单号: 10c2b0199c6a0315a1ce
									</view>
									<view>
										2020-04-13 12:03:17
									</view>
								</view>
							</view>
						</view>
					</view>
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
	.order-list{
		position: absolute;
		top: 90rpx;
		width: 100%;
		height: 100%;
		padding: 4px 8px;
		box-sizing: border-box;
		.order-card{
			margin-bottom: 8rpx;
			padding: 32rpx 12rpx 20rpx;
			background: #151b29;
			border-radius: 8rpx;
			font-size: 24rpx;
			text-align: left;
			color: #758bb5;
			.odds-detail{
				margin-bottom: 32rpx;
				border-bottom: 1px dashed #252f44;
				.odds-detail-header{
					position: relative;
					display: flex;
					align-items: center;
					padding-bottom: 12rpx;
					padding-left: 20rpx;
					padding-right: 20rpx;
					border-bottom: 1px solid #252f44;
					image{
						width: 40rpx;
						height: 40rpx;
					}
					.title{
						margin-left: 12rpx;
						color: #fff;
						font-size: 14px;
						word-break: break-word;
					}
					.type{
						margin-left: auto;
						text-align: right;
						word-break: keep-all
					}
					.flag-icon{
						position: absolute;
						right: 36rpx;
						bottom: -68rpx;
						background: url(../../static/images/icon30.svg) no-repeat;
						color: #cfdefc;
						display: flex;
						justify-content: center;
						align-items: center;
						background-position: 50%;
						background-repeat: no-repeat;
						width: 56rpx;
						height: 68rpx;
						font-weight: 700;
						font-size: 28rpx;
					}
				}
				.odds-detail-list{
					padding: 24rpx 20rpx;
					color: #526585;
				}
			}
			.order-info{
				padding-left: 20rpx;
				padding-right: 20rpx;
				.order-info-row{
					display: flex;
					justify-content: space-between;
					align-items: center;
					word-break: break-word;
					.order-title{
						color: #fff;
						font-size: 28rpx;
					}
					.order-status{
						padding-left: 12rpx;
						padding-right: 6rpx;
						border-radius: 4rpx;
						font-size: 28rpx;
						border: 1px solid #526585;
						color: #758bb5;
					}
					.order-info-row-lebal{
						color: #bacef1;
						.total-stake{
							color: #FFFFFF;
						}
						.bonus-lose{
							color: #758bb5;
						}
					}
				}
			}
		}
	}
</style>
