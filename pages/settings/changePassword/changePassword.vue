<template>
	<view class="change-password-page">
		<view class="form">
			<view class="base-input">
				<view class="input-label" :class="isActive1?'active':''">
					密码
				</view>
				<input type="text" placeholder="输入账户密码" placeholder-style="color:#5e7a96" @focus="focus(1)" @blur="blur(1)"/>
				<view class="focus-border" :class="isActive1?'active':''"></view>
			</view>
			<view class="base-input">
				<view class="input-label" :class="isActive2?'active':''">
					新密码
				</view>
				<input type="text" placeholder="请输入新密码" placeholder-style="color:#5e7a96" @focus="focus(2)" @blur="blur(2)"/>
				<view class="focus-border" :class="isActive2?'active':''"></view>
			</view>
			<view class="base-input">
				<view class="input-label" :class="isActive3?'active':''">
					确认密码
				</view>
				<input type="text" placeholder="再次输入相同密码" placeholder-style="color:#5e7a96" @focus="focus(3)" @blur="blur(3)"/>
				<view class="focus-border" :class="isActive3?'active':''"></view>
			</view>
			<view class="btn">
				确认
			</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				isActive1:false,
				isActive2:false,
				isActive3:false
			};
		},
		methods:{
			focus(index){
				if(index == 1){
					this.isActive1 = true
				}else if(index == 2){
					this.isActive2 = true
				} else{
					this.isActive3 = true
				}
			},
			blur(index){
				if(index == 1){
					this.isActive1 = false
				}else if(index == 2){
					this.isActive2 = false
				} else{
					this.isActive3 = false
				}
				
			}
		}
	}
</script>

<style lang="less">
uni-page-body{
	text-align: left;
	overflow: hidden;
}
.change-password-page{
	width: 100%;
	margin-top: 80rpx;
	display: flex;
	align-items: center;
	flex-direction: column;
	.form{
		width: calc(100% - 96rpx);
		.base-input{
			position: relative;
			text-align: left;
			width: 100%;
			white-space: nowrap;
			margin-bottom: 50rpx;
			display: flex;
			flex-direction: column;
			
			input{
				width: 100%;
				height: 64rpx;
				padding-left: 168rpx;
				color: #fff;
				caret-color: #1ffdfa;
				font-size: 30rpx;
				background: transparent;
				overflow: visible;
				resize: none;
				box-sizing: border-box;
			}
			.input-label{
				white-space: pre-line;
				word-break: break-word;
				position: absolute;
				left: 0;
				top: 14rpx;
				width: 136rpx;
				border-right: 1px solid #182031;
				background-color: transparent !important;
			}
			.focus-border{
				width: 100%;
				height: 1px;
				margin-top: 20rpx;
				background-color: #182031;
			}
			.active{
				color: rgb(30, 232, 231);
				background-color: #125e72;
			}
		}
	}
	.btn{
		width: 100%;
		height: 80rpx;
		line-height: 80rpx;
		border-radius: 8rpx;
		text-align: center;
		color: #5e7a96;
		border-radius: ;
		background-image: linear-gradient(90deg,#244053,#253c53);
		margin-top: 120rpx;
	}
}
</style>
