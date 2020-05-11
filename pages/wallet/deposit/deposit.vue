<template>
	<view class="deposit-page">
		<view class="form-deposit">
			<!-- <view class="payItem-list">
				<view class="card-padding">
					<view class="amount-input">
						<input type="text" value="" />
						<view class="input-label">
							金额
						</view>
						<text class="rmb-icon"></text>
						<view class="focus-border"></view>
					</view>
					<view class="amount-notice">
						单笔限额 ¥300 - 10000
					</view>
				</view>
			</view> -->
			<view class="payItem-list">
				<view class="">
					<view class="card-padding card-margin">
						金额
					</view>
					<view class="amount-checker-content">
						<view class="vux-checker-item">
							<view style="height: 4rpx;">&nbsp;</view>
							<view>
								<text class="amount-select">308</text>
								<text>元</text>
							</view>
							<view class="selected-checker-light"></view>
						</view>
						<view class="vux-checker-item">
							<view style="height: 4rpx;">&nbsp;</view>
							<view>
								<text class="amount-select">308</text>
								<text>元</text>
							</view>
							<view class="selected-checker-light"></view>
						</view>
						<view class="vux-checker-item">
							<view style="height: 4rpx;">&nbsp;</view>
							<view>
								<text class="amount-select">308</text>
								<text>元</text>
							</view>
							<view class="selected-checker-light"></view>
						</view>
						<view class="vux-checker-item">
							<view style="height: 4rpx;">&nbsp;</view>
							<view>
								<text class="amount-select">308</text>
								<text>元</text>
							</view>
							<view class="selected-checker-light"></view>
						</view>
					</view>
				</view>
			</view>
			<view class="submit-button">
				确认
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="less">
	.deposit-page{
		padding: 16rpx;
		width: 100%;
		box-sizing: border-box;
		.form-deposit{
			background: #151b29;
			border-radius: 8rpx;
			padding-top: 48rpx;
			padding-bottom: 48rpx;
			.payItem-list{
				display: flex;
				flex-direction: column;
				.card-padding{
					margin-bottom: 64rpx;
					padding-left: 32rpx;
					padding-right: 32rpx;
					text-align: left;
					.amount-input{
						position: relative;
						text-align: left;
						width: 100%;
						white-space: nowrap;
						margin-bottom: 16rpx;
						margin-top: 48rpx;
						display:flex;
						flex-direction: column;
						input{
							width: 100%;
							height: 128rpx;
							padding-left: 64rpx;
							border-radius: 0;
							color: #fff;
							caret-color: #1ffdfa;
							font-size: 60rpx;
							background: transparent;
							overflow: visible;
						}
						.input-label{
							position: absolute;
							top: -60rpx;
						}
						.rmb-icon{
							position: absolute;
							top: 46rpx;
							width: 32rpx;
							height: 40rpx;
							background: url(../../../static/images/icon32.svg);
						}
						.focus-border{
							width: 100%;
							height: 1px;
							margin-top: 20rpx;
							background-color: #252F44;
						}
					}
					.amount-notice{
						text-align: left;
						font-size: 24rpx;
						color: #758bb5;
					}
				}
				
				.card-margin{
					margin-bottom: 16rpx;
				}
				.amount-checker-content{
					width: 100%;
					display: flex;
					flex-wrap: wrap;
					margin-bottom: 40rpx;
					.vux-checker-item{
						box-sizing: border-box;
						width: calc((100vw - 80rpx) / 3);
						height: calc((100vw - 80rpx) / 3);
						margin: 8rpx;
						padding: 16rpx;
						display: flex;
						justify-content: space-between;
						align-items: center;
						flex-direction: column;
						text-align: center;
						background: #0c121f;
						border-radius: 8rpx;
						font-size: 24rpx;
						.amount-select{
							font-weight: bold;
							font-size: 48rpx;
						}
					}
					.selected-checker-light{
						width: 26px;
						height: 2px;
						background: #232d42;
					}
				}
			}
			.submit-button{
				margin-top: 52rpx;
				text-align: left;
				background-image: linear-gradient(90deg,#244053,#253c53);
				width: 100%;
				padding-left: 32rpx;
				padding-right: 32rpx;
				height: 80rpx;
				border-radius: 8rpx;
				display: flex;
				justify-content: center;
				align-items: center;
				box-sizing: border-box;
			}
		}
	}
</style>
