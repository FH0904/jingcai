<template>
	<view>
		<view class="list">
			<uni-list>
				<uni-list-item note="" :showArrow="false">
					<template>
						<view style="display: flex;align-items: center;"><text style="color: #bacef1;font-size: 28rpx;">姓名</text></view>
					</template>
					<template v-slot:right="">
						<text style="font-size: 28rpx;color: #fff;">fh</text>
					</template>
				</uni-list-item>
				<uni-list-item note="" @click="toNav('/pages/settings/changePhoneNumber/changePhoneNumber')">
					<template>
						<view style="display: flex;align-items: center;"><text style="color: #bacef1;font-size: 28rpx;">修改手机号码</text></view>
					</template>
					<template v-slot:right="">
						<text style="font-size: 28rpx;color: #fff;font-size: 32rpx;">13147102926</text>
					</template>
				</uni-list-item>
				<uni-list-item note="">
					<template>
						<view style="display: flex;align-items: center;"><text style="color: #bacef1;font-size: 28rpx;">生日</text></view>
					</template>
					<template v-slot:right="">
						<picker mode="date" :value="date" @change="bindDateChange">
							<text style="font-size: 28rpx;color: #fff;margin-right: 15rpx;" v-if="showTittle" >请选择你的生日</text>
							<view class="uni-input" v-else>{{ date }}</view>
						</picker>
					</template>
				</uni-list-item>
			</uni-list>
		</view>
		<view class="list">
			<uni-list>
				<uni-list-item note="" @click="toNav('/pages/settings/changePassword/changePassword')">
					<template>
						<view style="display: flex;align-items: center;"><text style="color: #bacef1;font-size: 28rpx;">修改密码</text></view>
					</template>
				</uni-list-item>
			</uni-list>
		</view>
		<view class="list">
			<uni-list>
				<uni-list-item note="" :showArrow="false">
					<template>
						<view style="display: flex;align-items: center;"><text style="color: #bacef1;font-size: 28rpx;">登出</text></view>
					</template>
				</uni-list-item>
			</uni-list>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		const currentDate = this.getDate({
			format: true
		});
		return {
			date: currentDate,
			showTittle:true
		};
	},
	methods: {
		toNav(url) {
			uni.navigateTo({
				url
			});
		},
		bindDateChange: function(e) {
			this.date = e.target.value;
			this.showTittle = false
		},
		getDate(type) {
			const date = new Date();
			let year = date.getFullYear();
			let month = date.getMonth() + 1;
			let day = date.getDate();

			if (type === 'start') {
				year = year - 60;
			} else if (type === 'end') {
				year = year + 2;
			}
			month = month > 9 ? month : '0' + month;
			day = day > 9 ? day : '0' + day;
			return `${year}-${month}-${day}`;
		}
	}
};
</script>

<style lang="less">
uni-page-body {
	background-color: #090c15;
}
.uni-list-item {
	background-color: #0c121f;
}
.list {
	padding-right: 26rpx;
	margin-bottom: 24px;
}
.uni-input{
	color: #fff;
}
</style>
