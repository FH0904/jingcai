<template>
	<view class="content">
		<view :class="isShowList ? 'router-view-click' : 'router-view'">
			<view class="filter-games">
				<view class="hide-filter-games-btn" style="visibility: hidden;">&nbsp;</view>
				<view>游戏筛选</view>
				<view class="hide-filter-games-btn" @click="close"><view class="btn-content">✓</view></view>
			</view>
			<view class="checker-content">
				<view class="selected-checker-item">
					<view style="height: 4rpx;">&nbsp;</view>
					<view class="games-info">
						<image src="/static/images/icon25.svg"></image>
						<view>全部</view>
					</view>
					<view class="selected-checker-light"></view>
				</view>
				<view class="selected-checker-item">
					<view style="height: 4rpx;">&nbsp;</view>
					<view class="games-info">
						<image src="/static/images/icon25.svg"></image>
						<view>全部</view>
					</view>
					<view class="selected-checker-light"></view>
				</view>
				<view class="selected-checker-item">
					<view style="height: 4rpx;">&nbsp;</view>
					<view class="games-info">
						<image src="/static/images/icon25.svg"></image>
						<view>全部</view>
					</view>
					<view class="selected-checker-light"></view>
				</view>
				<view class="selected-checker-item">
					<view style="height: 4rpx;">&nbsp;</view>
					<view class="games-info">
						<image src="/static/images/icon25.svg"></image>
						<view>全部</view>
					</view>
					<view class="selected-checker-light"></view>
				</view>
			</view>
		</view>
		<view class="tui-mtop">
			<tui-tabs :tabs="tabs" :currentTab="currentTab > 3 ? 0 : currentTab" bgColor="#090c15" @change="change" itemWidth="25%"></tui-tabs>
			<image src="/static/images/icon4.svg" mode="" class="tui-img" @click="close"></image>
			</view>
		<view class="tui-rolling-news">
			<image src="/static/images/icon5.svg" mode=""></image>
			<swiper vertical autoplay circular interval="3000" class="tui-swiper">
				<swiper-item v-for="(item, index) in newsList" :key="index" class="tui-swiper-item">
					<view class="tui-news-item" @tap="detail">{{ item }}</view>
				</swiper-item>
			</swiper>
		</view>
		<swiper class="swiper" :current="currentTab" :duration="300" @change="swiperChange" :style="'height:' + scrollH + 'px;'">
			<swiper-item v-for="(item, index) in tabs" :key="index">
				<view class="swiper-item">
					<scroll-view
						scroll-y="true"
						@scrolltolower="loadMore"
						:style="'height:' + scrollH + 'px;'"
						class="scroll-list"
						refresher-enabled="true"
						refresher-background="#090c15"
						:refresher-triggered="triggered"
						@refresherpulling="onPulling"
						@refresherrefresh="onRefresh"
						@refresherrestore="onRestore"
						@refresherabort="onAbort"
						:upper-threshold="200"
					>
						<view class="list">
							<view class="list-item" @click="toDetail">
								<view class="header">
									<image src="/static/images/icon6.svg" style="width: 40rpx;"></image>
									<text class="tournament-name">KPLGT职业联赛春季赛</text>
									<text class="match-round">/ BO5</text>
									<view class="play-count">+31</view>
								</view>
								<view class="body">
									<view class="body-team"><image src="/static/images/icon7.png" class="team-logo"></image></view>
									<view class="body-center">
										<image src="/static/images/icon9.svg" class="center-left"></image>
										<view class="team-score">
											<text class="score left-score">0</text>
											<text class="dash-symbol">-</text>
											<text class="score right-score">0</text>
										</view>
										<image src="/static/images/icon10.svg" class="center-right"></image>
									</view>
									<view class="body-team"><image src="/static/images/icon8.png" class="team-logo"></image></view>
								</view>
								<view class="odds-group-title">
									<view class="empty-badge">&nbsp;</view>
									<view class="title">全场获胜者</view>
								</view>
								<view class="card-footer">
									<view class="card-odds-btn">
										<view class="match-card-button btn-locked">
											<view class="button-dark-border">
												<view class="button-content">
													<view class="button-name">Sunrise</view>
													<image src="/static/images/icon11.svg" mode=""></image>
												</view>
											</view>
										</view>
									</view>
									<view class="match-status">
										<view class="match-is-live">
											<image src="/static/images/icon12.svg" mode=""></image>
											<view class="match-status-text">滚盘中</view>
										</view>
									</view>
									<view class="card-odds-btn">
										<view class="match-card-button btn-locked">
											<view class="button-dark-border">
												<view class="button-content">
													<view class="button-name">Sunrise</view>
													<image src="/static/images/icon11.svg" mode=""></image>
												</view>
											</view>
										</view>
									</view>
								</view>
							</view>
							<view class="list-item">
								<view class="header">
									<image src="/static/images/icon6.svg" style="width: 40rpx;"></image>
									<text class="tournament-name">KPLGT职业联赛春季赛</text>
									<text class="match-round">/ BO5</text>
									<view class="play-count">+31</view>
								</view>
								<view class="body">
									<view class="body-team"><image src="/static/images/icon7.png" class="team-logo"></image></view>
									<view class="body-center">
										<image src="/static/images/icon9.svg" class="center-left"></image>
										<view class="team-score">
											<text class="score left-score">0</text>
											<text class="dash-symbol">-</text>
											<text class="score right-score">0</text>
										</view>
										<image src="/static/images/icon10.svg" class="center-right"></image>
									</view>
									<view class="body-team"><image src="/static/images/icon8.png" class="team-logo"></image></view>
								</view>
								<view class="odds-group-title">
									<view class="empty-badge">&nbsp;</view>
									<view class="title">全场获胜者</view>
								</view>
								<view class="card-footer">
									<view class="card-odds-btn">
										<view class="match-card-button btn-locked">
											<view class="button-dark-border">
												<view class="button-content">
													<view class="button-name">Sunrise</view>
													<image src="/static/images/icon11.svg" mode=""></image>
												</view>
											</view>
										</view>
									</view>
									<view class="match-status">
										<view class="match-is-live">
											<image src="/static/images/icon12.svg" mode=""></image>
											<view class="match-status-text">滚盘中</view>
										</view>
									</view>
									<view class="card-odds-btn">
										<view class="match-card-button btn-locked">
											<view class="button-dark-border">
												<view class="button-content">
													<view class="button-name">Sunrise</view>
													<image src="/static/images/icon11.svg" mode=""></image>
												</view>
											</view>
										</view>
									</view>
								</view>
							</view>
							<view class="list-item">
								<view class="header">
									<image src="/static/images/icon6.svg" style="width: 40rpx;"></image>
									<text class="tournament-name">KPLGT职业联赛春季赛</text>
									<text class="match-round">/ BO5</text>
									<view class="play-count">+31</view>
								</view>
								<view class="body">
									<view class="body-team"><image src="/static/images/icon7.png" class="team-logo"></image></view>
									<view class="body-center">
										<image src="/static/images/icon9.svg" class="center-left"></image>
										<view class="team-score">
											<text class="score left-score">0</text>
											<text class="dash-symbol">-</text>
											<text class="score right-score">0</text>
										</view>
										<image src="/static/images/icon10.svg" class="center-right"></image>
									</view>
									<view class="body-team"><image src="/static/images/icon8.png" class="team-logo"></image></view>
								</view>
								<view class="odds-group-title">
									<view class="empty-badge">&nbsp;</view>
									<view class="title">全场获胜者</view>
								</view>
								<view class="card-footer">
									<view class="card-odds-btn">
										<view class="match-card-button btn-locked">
											<view class="button-dark-border">
												<view class="button-content">
													<view class="button-name">Sunrise</view>
													<image src="/static/images/icon11.svg" mode=""></image>
												</view>
											</view>
										</view>
									</view>
									<view class="match-status">
										<view class="match-is-live">
											<image src="/static/images/icon12.svg" mode=""></image>
											<view class="match-status-text">滚盘中</view>
										</view>
									</view>
									<view class="card-odds-btn">
										<view class="match-card-button btn-locked">
											<view class="button-dark-border">
												<view class="button-content">
													<view class="button-name">Sunrise</view>
													<image src="/static/images/icon11.svg" mode=""></image>
												</view>
											</view>
										</view>
									</view>
								</view>
							</view>
							<view class="list-item">
								<view class="header">
									<image src="/static/images/icon6.svg" style="width: 40rpx;"></image>
									<text class="tournament-name">KPLGT职业联赛春季赛</text>
									<text class="match-round">/ BO5</text>
									<view class="play-count">+31</view>
								</view>
								<view class="body">
									<view class="body-team"><image src="/static/images/icon7.png" class="team-logo"></image></view>
									<view class="body-center">
										<image src="/static/images/icon9.svg" class="center-left"></image>
										<view class="team-score">
											<text class="score left-score">0</text>
											<text class="dash-symbol">-</text>
											<text class="score right-score">0</text>
										</view>
										<image src="/static/images/icon10.svg" class="center-right"></image>
									</view>
									<view class="body-team"><image src="/static/images/icon8.png" class="team-logo"></image></view>
								</view>
								<view class="odds-group-title">
									<view class="empty-badge">&nbsp;</view>
									<view class="title">全场获胜者</view>
								</view>
								<view class="card-footer">
									<view class="card-odds-btn">
										<view class="match-card-button btn-locked">
											<view class="button-dark-border">
												<view class="button-content">
													<view class="button-name">Sunrise</view>
													<image src="/static/images/icon11.svg" mode=""></image>
												</view>
											</view>
										</view>
									</view>
									<view class="match-status">
										<view class="match-is-live">
											<image src="/static/images/icon12.svg" mode=""></image>
											<view class="match-status-text">滚盘中</view>
										</view>
									</view>
									<view class="card-odds-btn">
										<view class="match-card-button btn-locked">
											<view class="button-dark-border">
												<view class="button-content">
													<view class="button-name">Sunrise</view>
													<image src="/static/images/icon11.svg" mode=""></image>
												</view>
											</view>
										</view>
									</view>
								</view>
							</view>
							<view class="list-item">
								<view class="header">
									<image src="/static/images/icon6.svg" style="width: 40rpx;"></image>
									<text class="tournament-name">KPLGT职业联赛春季赛</text>
									<text class="match-round">/ BO5</text>
									<view class="play-count">+31</view>
								</view>
								<view class="body">
									<view class="body-team"><image src="/static/images/icon7.png" class="team-logo"></image></view>
									<view class="body-center">
										<image src="/static/images/icon9.svg" class="center-left"></image>
										<view class="team-score">
											<text class="score left-score">0</text>
											<text class="dash-symbol">-</text>
											<text class="score right-score">0</text>
										</view>
										<image src="/static/images/icon10.svg" class="center-right"></image>
									</view>
									<view class="body-team"><image src="/static/images/icon8.png" class="team-logo"></image></view>
								</view>
								<view class="odds-group-title">
									<view class="empty-badge">&nbsp;</view>
									<view class="title">全场获胜者</view>
								</view>
								<view class="card-footer">
									<view class="card-odds-btn">
										<view class="match-card-button btn-locked">
											<view class="button-dark-border">
												<view class="button-content">
													<view class="button-name">Sunrise</view>
													<image src="/static/images/icon11.svg" mode=""></image>
												</view>
											</view>
										</view>
									</view>
									<view class="match-status">
										<view class="match-is-live">
											<image src="/static/images/icon12.svg" mode=""></image>
											<view class="match-status-text">滚盘中</view>
										</view>
									</view>
									<view class="card-odds-btn">
										<view class="match-card-button btn-locked">
											<view class="button-dark-border">
												<view class="button-content">
													<view class="button-name">Sunrise</view>
													<image src="/static/images/icon11.svg" mode=""></image>
												</view>
											</view>
										</view>
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
import tuiTabs from '@/components/tui-tabs/tui-tabs';
export default {
	comments: {
		tuiTabs
	},
	data() {
		return {
			tabs: [
				{
					name: '今日 42'
				},
				{
					name: '滚盘 1'
				},
				{
					name: '赛前 82'
				},
				{
					name: '已结束'
				}
			],
			currentTab: 0,
			newsList: ['DOTA2  亚洲春季邀请赛  KG - VS - Geek Fam  赛事未进行', 'DOTA2  亚洲春季邀请赛  KG - VS - Geek Fam  赛事未进行', 'DOTA2  亚洲春季邀请赛  KG - VS - Geek Fam  赛事未进行'],
			scrollH: 500,
			isShowList: true,
			triggered: false
		};
	},
	onLoad(options) {
		//获取可视区域的高度
		uni.getSystemInfo({
			success: res => {
				console.log(res);
				this.scrollH = res.windowHeight - uni.upx2px(186);
			}
		});
		this._freshing = false;
		setTimeout(() => {
			this.triggered = true;
		}, 1000);
	},
	methods: {
		change(e) {
			this.currentTab = e.index;
			this._freshing = false;
			setTimeout(() => {
				this.triggered = true;
			}, 1000);
			console.log(1);
		},
		detail(e) {
			console.log(e);
		},
		loadMore() {
			console.log('到底了');
		},
		// 滑动切换
		swiperChange(data) {
			this.currentTab = data.detail.current;
		},
		// 去详情
		toDetail() {
			uni.navigateTo({
				url: '/pages/detail/detail'
			});
		},
		close() {
			this.isShowList = !this.isShowList;
		},
		onRefresh() {
			if (this._freshing) return;
			this._freshing = true;
			setTimeout(() => {
				this.triggered = false;
				this._freshing = false;
			}, 3000);
		},
		onRestore() {
			this.triggered = false; // 需要重置
			console.log('onRestore');
		},
		onAbort() {
			console.log('onAbort');
		},
		onPulling(e) {
			this._freshing = false;
			setTimeout(() => {
				this.triggered = true;
			}, 1000);
		}
	},

	onNavigationBarButtonTap(e) {
		if (e.index == 1) {
			uni.navigateTo({
				url: '/pages/personal/personal'
			});
		}
	}
};
</script>

<style lang="less">
.tui-mtop {
	height: 86rpx;
	position: relative;
}
.tui-img{
	position: absolute;
	right: 0;
	top: 0;
	bottom: 0;
	margin: auto;
	width: 90rpx;
	height: 78rpx;
}
.swiper {
	margin-top: 100rpx;
}
.router-view-click {
	position: fixed;
	bottom: -2000rpx;
	left: 0;
	width: 100%;
	height: 100%;
	background-color: #0c121f;
	z-index: 9999;
	transition-property: transform;
	transition-duration: 0.3s;
}
.router-view {
	position: fixed;
	top: 88rpx;
	left: 0;
	width: 100%;
	height: 100%;
	background-color: #0c121f;
	z-index: 9999;
	.filter-games {
		width: 100%;
		height: 86rpx;
		padding-right: 16rpx;
		padding-left: 16rpx;
		display: flex;
		-ms-flex-pack: justify;
		justify-content: space-between;
		align-items: center;
		background-color: #090c15;
		font-size: 26rpx;
		box-sizing: border-box;
		border-bottom: 1px solid #182031;
		.hide-filter-games-btn {
			border-radius: 4rpx;
			display: flex;
			justify-content: center;
			align-items: center;
			width: 96rpx;
			height: 40rpx;
			background: linear-gradient(90deg, #0689f3, #019bbd);
			.btn-content {
				width: calc(100% - 4rpx);
				height: 36rpx;
				background: #151b29;
				color: #1ee8e7;
			}
		}
	}
	.checker-content {
		display: flex;
		flex-wrap: wrap;
		padding: 8rpx;
		box-sizing: border-box;
		.selected-checker-item {
			box-sizing: border-box;
			flex-direction: column;
			display: flex;
			align-items: center;
			width: calc((100vw - 64rpx) / 3);
			height: calc((100vw - 64rpx) / 3);
			margin: 8rpx;
			padding: 16rpx;
			text-align: center;
			font-size: 24rpx;
			background: #151b29;
			color: #526585;
			border-radius: 8rpx;
			justify-content: space-between;
			.games-info {
				flex-direction: column;
				display: flex;
				align-items: center;
				justify-content: center;
				image {
					margin: 16rpx;
					width: 56rpx;
					height: 56rpx;
				}
			}
			.selected-checker-light {
				width: 52rpx;
				height: 4rpx;
				background: #232d42;
			}
		}
	}
}
.tui-rolling-news {
	position: fixed;
	left: 0;
	right: 0;
	margin-left: 16rpx;
	margin-right: 16rpx;
	height: 100rpx;
	display: flex;
	justify-content: center;
	align-items: center;
	background-color: #0c121f;
	border-bottom: 1px solid #182031;
	font-size: 24rpx;
	color: #00befe;
	z-index: 10;
	image {
		width: 36rpx;
		height: 36rpx;
		margin-left: 32rpx;
		margin-right: 16rpx;
	}
	.tui-swiper {
		font-size: 24rpx;
		height: 80rpx;
		width: 100%;
		flex: 1;
		.tui-swiper-item {
			display: flex;
			align-items: center;
			.tui-news-item {
				line-height: 80upx;
				white-space: nowrap;
				overflow: hidden;
				text-overflow: ellipsis;
			}
		}
	}
}
.scroll-list {
	padding: 0 16rpx;
	box-sizing: border-box;
	.list-item {
		height: 416rpx;
		background: #1d2638;
		border-radius: 8px;
		padding: 4rpx 32rpx 36rpx;
		margin: 16rpx 0;
		position: relative;
		border-top: 1px solid #1c3545;
		background-image: linear-gradient(#1c3545, #1d2638 10%), linear-gradient(#1c3545, #1d2638 10%);
		background-size: 1px 100%;
		background-position: 0 0, 100% 0;
		background-repeat: no-repeat;
		box-sizing: border-box;
		.header {
			height: 74rpx;
			display: flex;
			align-items: center;
			font-size: 24rpx;
			.tournament-name {
				white-space: nowrap;
				text-overflow: ellipsis;
				overflow: hidden;
				margin-left: 12rpx;
				padding-top: 20rpx;
				padding-bottom: 20rpx;
				color: #bacef1;
			}
			.match-round {
				white-space: nowrap;
				text-overflow: ellipsis;
				overflow: hidden;
				text-overflow: unset;
				color: #758bb5;
				margin-left: 14rpx;
			}
			.play-count {
				display: flex;
				align-items: center;
				width: 60rpx;
				height: 40rpx;
				margin-left: auto;
				background: #182032;
				border: 1px solid #1c5d94;
				border-radius: 4rpx;
				font-size: 24rpx;
				color: #1ad2fe;
				justify-content: center;
				line-height: normal;
			}
		}
		.body {
			display: flex;
			margin-top: 12rpx;
			margin-bottom: 16rpx;
			justify-content: space-between;
			.body-team {
				display: flex;
				justify-content: center;
				width: 29.86667vw;
				.team-logo {
					display: inline-block;
					background-position: 50%;
					background-repeat: no-repeat;
					width: 144rpx;
					height: 144rpx;
				}
			}
			.body-center {
				width: 27.46667vw;
				display: flex;
				justify-content: center;
				align-items: center;
				position: relative;
				.team-score {
					display: flex;
					justify-content: space-between;
					align-items: center;
					font-size: 56rpx;
					color: #fff;
					position: relative;
					z-index: 1;
					.score {
						position: absolute;
					}
					.left-score {
						font-family: AlphaH;
						right: 0;
						margin-right: 48rpx;
					}
					.dash-symbol {
						color: #758bb5;
					}
					.right-score {
						font-family: AlphaH;
						left: 0;
						margin-left: 24px;
					}
				}
				.center-left {
					position: absolute;
					left: -48rpx;
					width: 48rpx;
					height: 156rpx;
				}
				.center-right {
					position: absolute;
					right: -48rpx;
					width: 48rpx;
					height: 156rpx;
				}
			}
		}
		.odds-group-title {
			height: 34rpx;
			display: flex;
			align-items: center;
			text-align: left;
			.empty-badge {
				width: 4rpx;
				height: 18rpx;
				background: #bacef1;
			}
			.title {
				font-size: 24rpx;
				color: #bacef1;
				margin: 0 16rpx 0 8rpx;
			}
		}
		.card-footer {
			margin-top: 14rpx;
			display: flex;
			justify-content: space-between;
			align-items: center;
			.card-odds-btn {
				width: 29.86667vw;
				.match-card-button {
					width: 100%;
					height: 80rpx;
					display: flex;
					justify-content: center;
					align-items: center;
					border-radius: 8rpx;
					background: linear-gradient(90deg, #298a97, #317699);
					box-shadow: 0 0 8rpx 0 rgba(14, 20, 34, 0.5);
					.button-dark-border {
						display: flex;
						justify-content: center;
						align-items: center;
						width: calc(100% - 2px);
						background: linear-gradient(#323e57, #1d2639);
						height: 38px;
						border-radius: 3px;
						.button-content {
							border-radius: 4rpx;
							background-color: #252f44;
							flex-direction: column;
							height: 72rpx;
							display: flex;
							justify-content: center;
							align-items: center;
							width: calc(100% - 2px);
							.button-name {
								font-size: 24rpx;
								color: #bacef1;
							}
							image {
								width: 20rpx;
								height: 20rpx;
								margin-top: 8rpx;
							}
						}
					}
				}
			}
			.match-status {
				width: 27.46667vw;
				font-size: 24rpx;
				align-self: flex-start;
				.match-is-live {
					display: flex;
					justify-content: center;
					align-items: center;
					flex-direction: column;
					.match-status-text {
						color: #1ffdfa;
					}
					image {
						width: 24px;
						height: 24px;
					}
				}
			}
		}
	}
}
</style>
