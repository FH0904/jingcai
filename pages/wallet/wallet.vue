<template>
	<view class="wallet">
		<view class="wallet-header">
			<view class="header-text">
				钱包余额
			</view>
			<view class="header-money">
				0.00
			</view>
			<view class="withdrawal-button" @click="toNav('/pages/wallet/addBankCard/addBankCard')">
				<view class="button-content">
					提款
				</view>
			</view>
		</view>
		<view class="wallet-body">
			<view class="table-title">
				选择付款方式
			</view>
			<view class="grid-content">
				<view class="grid-item" v-for="(item,index) in gridData" :key="index">
					<image :src="item.img" mode=""></image>
					<view class="grid-text">
						{{item.text}}
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				gridData:[
					{
						img:'/static/images/icon26.svg',
						text:'支付宝'
					},
					{
						img:'/static/images/icon27.svg',
						text:'银联支付'
					},
					{
						img:'/static/images/icon28.svg',
						text:'充值卡'
					},
					{
						img:'/static/images/icon29.svg',
						text:'网银支付'
					},
					{
						img:'/static/images/icon26.svg',
						text:'支付宝转卡'
					},
				]
			}
		},
		methods:{
			toNav(url){
				uni.navigateTo({
					url
				})
			}
		}
	}
</script>

<style lang="less">
	.wallet-header{
		display: flex;
		align-items: center;
		flex-direction: column;
		width: 100%;
		.header-text{
			margin-top: 32rpx;
			font-size: 24rpx;
			color: #526585;
		}
		.header-money{
			font-size: 84rpx;
			color: #fff;
			line-height: 118rpx;
			font-weight: 300;
		}
		.withdrawal-button{
			display: flex;
			justify-content: center;
			align-items: center;
			border-radius: 200rpx;
			padding: 1px;
			margin-top: 24rpx;
			margin-bottom: 64rpx;
			background: linear-gradient(90deg,#0689f3,#019bbd);
			color: #2197f4;
			box-sizing: border-box;
			.button-content{
				min-width: 160rpx;
				padding: 14rpx 52rpx;
				background: #151b29;
				box-sizing: border-box;
				display: flex;
				justify-content: center;
				align-items: center;
				border-radius: 200rpx;
			}
		}
	}
	.wallet-body{
		.table-title{
			height: 64rpx;
			font-size: 24rpx;
			padding-left: 32rpx;
			background-color: #182032;
			display: flex;
			align-items: center;
			box-sizing: border-box;
		}
		.grid-content{
			display: flex;
			flex-wrap: wrap;
			background: #182032;
			border-left: 1px solid #1d2638;
			border-top: 1px solid #1d2638;
			box-sizing: border-box;
			.grid-item{
				width: 33.33%;
				height: 224rpx;
				display: flex;
				justify-content: center;
				align-items: center;
				flex-direction: column;
				background-color: #182032;
				border-bottom: 1px solid #1d2638;
				border-right: 1px solid #1d2638;
				box-sizing: border-box;
				image{
					width: 70rpx;
					height: 70rpx;
				}
				.grid-text{
					font-size: 24rpx;
					color: #FFFFFF;
					margin-top: 20rpx;
				}
			}
		}
	}
</style>
