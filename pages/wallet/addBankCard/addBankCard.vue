<template>
	<view class="Card">
		<view class="img">
			<image src="../../../static/images/fl-icon.d122ca9a.png" mode=""></image>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			percent:100
		};
	},
	onLoad() {
		this.a()
	},
	methods:{
		a(){
			setInterval(()=>{
				this.percent --
			},1000)
		}
	}
};
</script>

<style lang="less">
.Card{
	position: relative;
	width: 100%;
	height: 100%;
	background: url(../../../static/images/map_fd.fd2b7a07.png) no-repeat;
	background-size: contain;
	background-position: bottom;
}
.img{
	position: absolute;
	bottom: 0;
	right: 0;
	width: 70rpx;
	height: 70rpx;
	animation: move 10s linear infinite;
}
image{
	width: 70rpx;
	height: 70rpx;
}
@keyframes move {
	0%{
		right: 0;
		bottom: 0;
	}
	3%{
		right: 30rpx;
		bottom: 10rpx;
	}
	5%{
		right: 50rpx;
		bottom: 20rpx;
	}
	8%{
		right: 90rpx;
		bottom: 35rpx;
	}
	10%{
		right: 120rpx;
		bottom: 50rpx;
	}
	15%{
		right: 170rpx;
		bottom: 130rpx;
	}
	20%{
		right: 190rpx;
		bottom: 240rpx;
	}
	25%{
		right: 176rpx;
		bottom: 320rpx;
	}
	30%{
		right: 148rpx;
		bottom: 410rpx;
	}
	35%{
		right: 168rpx;
		bottom: 510rpx;
	}
	40%{
		right: 314rpx;
		bottom: 560rpx;
	}
	45%{
		right: 434rpx;
		bottom: 560rpx;
	}
	50%{
		right: 532rpx;
		bottom: 506rpx;
	}
	55%{
		right: 564rpx;
		bottom: 388rpx;
	}
	60%{
		right: 552rpx;
		bottom: 288rpx;
	}
	70%{
		right: 552rpx;
		bottom: 190rpx;
	}
	80%{
		right: 586rpx;
		bottom: 98rpx;
	}
	90%{
		right: 632rpx;
		bottom: 30rpx;
	}
	100%{
		right: 100vw;
		bottom: 0;
	}
	}
</style>
