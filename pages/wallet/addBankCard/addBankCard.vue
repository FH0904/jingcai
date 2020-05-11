<template>
	<view class="add-bank-card-page">
		<view class="form-card">
			<view class="card-header">
				<view>持卡人</view>
				<view class="name-content">
					<view class="user-name">哈哈</view>
					<view class="note">持卡人姓名需与注册帐号一致</view>
				</view>
			</view>
			<view class="card-body">
				<view class="amount-input card-input">
					<input type="text" placeholder="请输入卡号" placeholder-style="font-size:28rpx;color: #758bb5;" />
					<label class="input-label">卡号</label>
					<view class="focus-border"></view>
				</view>
				<view class="base-input">
					<view class="input">
						<picker @change="bindPickerChange" :value="index" :range="array">
							<view class="uni-input">{{ array[index] }}</view>
						</picker>
					</view>
					<view class="input-label">开户银行</view>
					<image src="../../../static/images/icon31.svg" mode="" class="right-icon"></image>
					<view class="focus-border"></view>
				</view>
				<view class="base-button">确认</view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data(){
		return{
			index:0,
			array: ['中国', '美国', '巴西', '日本'],
		}
	},
	methods:{
	 bindPickerChange(e){
		this.index = e.target.value
	},
	}
};
</script>

<style lang="less">
	uni-picker{
		width: 100%;
	}
.add-bank-card-page {
	padding: 8px;
	box-sizing: border-box;
	.form-card {
		background: #151b29;
		border-radius: 8rpx;
		.card-header {
			display: flex;
			background: #182032;
			border-radius: 8rpx 8rpx 0 0;
			padding-left: 32rpx;
			padding-top: 40rpx;
			padding-bottom: 20rpx;
			.name-content {
				display: flex;
				flex-direction: column;
				text-align: left;
				margin-left: 76rpx;
				.user-name {
					color: #ffffff;
				}
				.note {
					margin-top: 8rpx;
					font-size: 24rpx;
					color: #758bb5;
				}
			}
		}
		.card-body {
			padding: 48rpx 32rpx;
			.amount-input {
				position: relative;
				text-align: left;
				width: 100%;
				white-space: nowrap;
				margin-bottom: 16rpx;
				margin-top: 48rpx;
				display: flex;
				flex-direction: column;
			}
			.card-input {
				margin-bottom: 64rpx;
				input {
					width: 100%;
					height: 60rpx;
					padding-left: 0;
					border-radius: 0;
					color: #fff;
					caret-color: #1ffdfa;
					font-size: 44rpx;
					background: transparent;
					outline: none;
					border: none;
					overflow: visible;
				}
				.input-label {
					position: absolute;
					top: -30px;
				}
				.focus-border {
					width: 100%;
					height: 1px;
					margin-top: 20rpx;
					background-color: #252f44;
				}
			}
			.base-input {
				position: relative;
				text-align: left;
				width: 100%;
				white-space: nowrap;
				margin-bottom: 50rpx;
				display: flex;
				flex-direction: column;
				.input {
					display: flex;
					align-items: center;
					width: 100%;
					height: 64rpx;
					padding-left: 168rpx;
					border-radius: 0;
					color: #fff;
					caret-color: #1ffdfa;
					font-size: 30rpx;
					background: transparent;
					outline: none;
					border: none;
					overflow: visible;
					resize: none;
				}
				.input-label {
					white-space: pre-line;
					word-break: break-word;
					position: absolute;
					left: 0;
					top: 14rpx;
					width: 136rpx;
					border-right: 1px solid #182031;
					border-color: #252f44;
				}
				.right-icon {
					background-position: 50%;
					background-repeat: no-repeat;
					width: 52rpx;
					height: 52rpx;
					position: absolute;
					top: 4rpx;
					right: 0;
					box-sizing: border-box;
				}
				.focus-border {
					width: 100%;
					height: 1px;
					margin-top: 20rpx;
					background-color: #252f44;
				}
			}
			.base-button {
				background-image: linear-gradient(90deg, #244053, #253c53);
				width: 100%;
				height: 80rpx;
				margin: 16rpx 0;
				border-radius: 8rpx;
				display: flex;
				justify-content: center;
				align-items: center;
			}
		}
	}
}
</style>
