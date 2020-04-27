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
					电话
				</view>
				<input type="text" placeholder="填写手机号" placeholder-style="color:#5e7a96" v-model="tel" @focus="focus(2)" @blur="blur(2)" @input="input"/>
				<view class="focus-border" :class="isActive2?'active':''"></view>
				<view class="send-code-btn" :class="isActive4?'enabled':''" @click="getVerCode">
					{{verCodeText}}
				</view>
			</view>
			<view class="base-input">
				<view class="input-label" :class="isActive3?'active':''">
					验证码
				</view>
				<input type="text" placeholder="输入验证码" placeholder-style="color:#5e7a96" @focus="focus(3)" @blur="blur(3)"/>
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
				isActive3:false,
				isActive4:false,
				tel:'',
				verCodeText:"获取验证码"
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
				
			},
			input(){
				if(this.tel.length == 11){
					this.isActive4 = true
				}else if(this.tel.length < 11){
					this.isActive4 = false
				}
			},
			// 获取验证码
			async getVerCode() {
			  let intervalTime = 10;
			  // let a = await this.$http.getCode({
			  //   phone: this.phoneText
			  // });
			
			  uni.showToast({
			    title: '验证码发送成功',
			    icon: 'none'
			  });
			  this.isActive4 = false;
			  let intervalId = setInterval(() => {
			    intervalTime--;
			    this.verCodeText = `${intervalTime}秒`
			    if (intervalTime <= 0) {
			      clearInterval(intervalId)
			      this.verCodeText = "获取验证码"
			      this.isActive4 = true;
			    }
			  }, 1000)
			},
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
			.send-code-btn{
				height: 52rpx;
				color: #526585;
				background: #182032;
				border: 1px solid #27394c;
				border-radius: 4rpx;
				position: absolute;
				margin-top: 8rpx;
				right: 0;
				font-size: 24rpx;
				display: flex;
				justify-content: center;
				align-items: center;
				outline: 0;
				padding: 0 10rpx;
			}
			.enabled{
				border: 1px solid #0585a1;
				color: #fff;
				transition: border .5s,color .5s;
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
