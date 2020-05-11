<template>
	<view class="personal">
		<view class="list">
			<view class="list_item1">
				<view class="item1">
					<view class="item1_text">
						<view class="text1">
							晚上好
						</view>
						<view class="text2">
							FH0904
						</view>
					</view>
				</view>
				<uni-list>
					<uni-list-item note="">
						<template>
						    <view style="display: flex;align-items: center;" @click="toNav('/pages/wallet/wallet')">
						    	<image style="width: 44rpx;height: 44rpx;margin-right: 30rpx;" src="/static/images/icon13.svg"></image>
						    	<text style="color: #bacef1;font-size: 28rpx;">钱包</text>
						    </view>
						</template>
						<template v-slot:right="">
						    <text style="font-size: 24rpx;color: #526585;">余额</text>
							<text style="font-size: 32rpx;color: #1ee8e7;">￥0.00</text>
						</template>
					</uni-list-item>
				</uni-list>
			</view>
		</view>
		<view class="list">
			<view class="list_item2">
				<uni-list>
					<uni-list-item  note="">
						<template>
						    <view style="display: flex;align-items: center;" @click="toNav('/pages/betsHistory/betsHistory')">
						    	<image style="width: 44rpx;height: 44rpx;margin-right: 30rpx;" src="/static/images/icon14.svg"></image>
						    	<text style="color: #bacef1;font-size: 28rpx;">投注记录</text>
						    </view>
						</template>
					</uni-list-item>
				</uni-list>
				<uni-list>
					<uni-list-item  note="">
						<template>
						    <view style="display: flex;align-items: center;">
						    	<image style="width: 44rpx;height: 44rpx;margin-right: 30rpx;" src="/static/images/icon15.svg"></image>
						    	<text style="color: #bacef1;font-size: 28rpx;">消息</text>
						    </view>
						</template>
					</uni-list-item>
				</uni-list>
				<uni-list>
					<uni-list-item  note="">
						<template>
						    <view style="display: flex;align-items: center;" @click="toNav('/pages/personal/activities/activities')">
						    	<image style="width: 44rpx;height: 44rpx;margin-right: 30rpx;" src="/static/images/icon16.svg"></image>
						    	<text style="color: #bacef1;font-size: 28rpx;">活动</text>
						    </view>
						</template>
					</uni-list-item>
				</uni-list>
			</view>
		</view>
		<view class="list">
			<view class="list_item2">
				<uni-list>
					<uni-list-item  note="">
						<template>
						    <view style="display: flex;align-items: center;">
						    	<image style="width: 44rpx;height: 44rpx;margin-right: 30rpx;" src="/static/images/icon17.svg"></image>
						    	<text style="color: #bacef1;font-size: 28rpx;">玩法规则</text>
						    </view>
						</template>
					</uni-list-item>
				</uni-list>
				<uni-list>
					<uni-list-item  note="">
						<template>
						    <view style="display: flex;align-items: center;">
						    	<image style="width: 44rpx;height: 44rpx;margin-right: 30rpx;" src="/static/images/icon18.svg"></image>
						    	<text style="color: #bacef1;font-size: 28rpx;">关于我们</text>
						    </view>
						</template>
					</uni-list-item>
				</uni-list>
				<uni-list>
					<uni-list-item  note="" :showArrow="false">
						<template>
						    <view style="display: flex;align-items: center;">
						    	<image style="width: 44rpx;height: 44rpx;margin-right: 30rpx;" src="/static/images/icon18.svg"></image>
						    	<text style="color: #bacef1;font-size: 28rpx;">版本</text>
						    </view>
						</template>
						<template v-slot:right="">
						    <text style="font-size: 28rpx;color: #526585;">v 2.0.30（157）</text>
						</template>
					</uni-list-item>
				</uni-list>
			</view>
		</view>
		<view class="btn">
			<view class="btn1">
				<text>推荐</text>
			</view>
			<view class="btn1">
				<text>代理</text>
			</view>
			<view class="btn1">
				<text>联系</text>
			</view>
		</view>
	</view>
</template>

<script>
	import uniList from "@/components/uni-list/uni-list.vue"
	import uniListItem from "@/components/uni-list-item/uni-list-item.vue"
	export default {
	    components: {uniList,uniListItem},
		methods:{
			toNav(url){
				uni.navigateTo({
					url
				})
			}
		},
		onNavigationBarButtonTap(e) {
			if(e.index==0){
				uni.navigateTo({
					url:"/pages/settings/settings"
				})
			}
		}
		
	}
</script>

<style lang="less">
	page{
		background-color: #090c15;
	}
	.uni-list-item{
		padding: 0;
		background-color: #0c121f;
	}
	.uni-list-item--first{
		padding-right: 0;
	}
	.uni-icons{
		color: #3f546a;
	}
	.list{
		margin-bottom: 24px;
		background-color: #0c121f!important;
		.list_item2{
			padding: 0 30rpx 0 20rpx;
			box-sizing: border-box;
			background-color: #0c121f;
		}
		.list_item1{
			padding: 0px 30rpx;
			padding: 0 30rpx 0 20rpx;
			box-sizing: border-box;
			background-color: #0c121f;
			.item1{
				display: flex;
				align-items: center;
				height: 226rpx;
				.item1_text{
					flex: 1;
					/* #ifdef APP-PLUS */
					padding-left: 26rpx;
					box-sizing: border-box;
					/* #endif */
					.text1{
						color: #758bb5;
						font-size: 24rpx;
						text-align: left;
					}
					.text2{
						color: #bacef1;
						font-size: 36rpx;
						line-height: 52rpx;
						text-align: left;
					}
				}
			}
			
		}
	}
	.btn{
		width: 100%;
		display: flex;
		justify-content: space-around;
		.btn1{
			box-sizing: border-box;
			display: flex;
			justify-content: center;
			align-items: center;
			width: 160rpx;
			height: 64rpx;
			background-color: #090c15;
			border: 1px solid #182031;
			border-radius: 8rpx;
			font-size: 26rpx;
			color: #7589a6;
			text-decoration: none;
		}
	}
</style>
