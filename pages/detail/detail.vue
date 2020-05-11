<template>
	<view class="detail">
		<view class="betting-info">
			<view class="info-title">
				<image src="/static/images/icon19.svg" mode=""></image>
				<text class="tournament-name">CK春季赛</text>
				<text class="match-round"> / BO3</text>
			</view>
			<view class="info-team">
				<view class="team-info">
					<image src="/static/images/icon20.png" mode="" class="team-logo"></image>
					<view class="team-name">Asura</view>
				</view>
				<view class="betting-status">
					<view class="status-early">
						<view class="is-early">
							<view class="match-date">
								4月 16日 周四
							</view>
							<view class="match-time">
								13:00
							</view>
						</view>
					</view>
					<view class="is-raedy">
						未开始
					</view>
				</view>
				<view class="team-info">
					<image src="/static/images/icon21.png" mode="" class="team-logo"></image>
					<view class="team-name">Asura</view>
				</view>
			</view>
		</view>
		<video src="https://rayapi.livet.cn/m3u8url/raybet?url=https%3A%2F%2Fwww.douyu.com%2F8092994&teams=DW-ORD" controls></video>
		<view class="tui-mtop"><tui-tab :tabs="tabs" :currentTab="currentTab > 3 ? 0 : currentTab" bgColor="#090c15" @change="change" itemWidth="150rpx" ></tui-tab></view>
		<scroll-view scroll-y="true" :style="'height:'+ scrollH +'px;'" class="scroll">
			<view class="betting-odds">
				<view class="stage-title">
					全场
				</view>
				<view class="group-list">
					<view class="odds-group-title">
						<view class="empty-badge"></view>
						<view class="title">
							获胜者
						</view>
					</view>
					<view class="group-odds">
						<view class="odds-btn" :class="isSelected?'btn-selected1':''">
							<view class="button-dark-border" @click="selected" :class="isSelected?'btn-selected':''">
								<view class="btn-left">
									<view class="button-name" >
										BLG
									</view>
									<view class="button-odds-content">
										1.11
									</view>
								</view>
							</view>
						</view>
						<view class="odds-btn">
							<view class="button-dark-border">
								<view class="btn-left">
									<view class="button-name">
										BLG
									</view>
									<view class="button-odds-content">
										1.11
									</view>
								</view>
							</view>
						</view>
					</view>
				</view>
				<view class="group-list">
					<view class="odds-group-title">
						<view class="empty-badge"></view>
						<view class="title">
							获胜者
						</view>
					</view>
					<view class="group-odds">
						<view class="odds-btn">
							<view class="button-dark-border">
								<view class="btn-left">
									<view class="button-name">
										BLG
									</view>
									<view class="button-odds-content">
										1.11
									</view>
								</view>
							</view>
						</view>
						<view class="odds-btn">
							<view class="button-dark-border">
								<view class="btn-left">
									<view class="button-name">
										BLG
									</view>
									<view class="button-odds-content">
										1.11
									</view>
								</view>
							</view>
						</view>
					</view>
				</view>
			</view>
		</scroll-view>
		
		<view class="tab-content" @click="close">
			<view class="selected-text" v-if="isClose === true">
				<view>投注单</view>
				<view class="selected-number">1</view>
			</view>
			<view class="bet-amount" v-else>
				<view>
					投注金额 0.00
				</view>
				<view class="">
					最高返还
					<text class="total-return">0.00</text>
				</view>
			</view>
			<view class="toggle-tab">
				<view v-if="isClose === true">
					展开
				</view>
				<view v-else>
					收起
				</view>
			</view>
			<view class="bet-btn ">
				<view v-if="isClose === true">
					投注单
				</view>
				<view v-else>
					确认投注
				</view>
			</view>
		</view>
		<view class="bet-slip-pop" :class="isClose?'close1':'close2'">
			<view class="bet-slip-pop-header">
				<view class="slip-number">
					1
				</view>
				<view class="remove-all">
					删除全部
				</view>
				<view class="pop-header-text">
					<view class="pop-header-balance">
						余额
					</view>
					<view>0.00</view>
				</view>
				<view class="pop-header-close" @click="close"></view>
			</view>
			<view class="bet-slip-pop-body">
				<view class="__vuescroll">
					<scroll-view scroll-y="true" class="__slide" >
						<view class="odds-list">
							<view class="odds-item" @click="showKeyboard">
								<view class="odds-list-line"></view>
								<view class="remove-odds">
									<view class="remove-odds-icon"></view>
								</view>
								<view class="odds-item-match">
									<view class="odds-name">
										否
									</view>
									<view>
										第二局 出现超级兵
									</view>
									<view>
										IG - VS - VG
									</view>
								</view>
								<view class="odds-item-money">
									<view class="item-money">
										<view class="money-odds">
											@1.16
										</view>
										<view class="stake-input " :class="input_focus?'stake-input-focus':''">
											<text class="input-text" :class="direction?'input-text-focus-left':'input-text-focus-right'">
												{{amount}}
											</text>
										</view>
									</view>
									<view class="item-return">
										预计返还
										<text class="return-amount">1.16</text>
									</view>
								</view>
							</view>
							<view :class="keyboard_active?'keyboard-item':'keyboard-item-active'">
								<view class="bet-keyboard">
									<view class="content">
										<view class='content__btn--number' @click="tab(1)">1</view>
										<view class='content__btn--number' @click="tab(2)">2</view>
										<view class='content__btn--number' @click="tab(3)">3</view>
										<view class='content__btn--number' @click="tab(4)">4</view>
										<view class='content__btn--number' @click="tab(5)">5</view>
										<view class='content__btn--number' @click="tab(6)">6</view>
										<view class='content__btn--number' @click="tab(7)">7</view>
										<view class='content__btn--number' @click="tab(8)">8</view>
										<view class='content__btn--number' @click="tab(9)">9</view>
										<view class='content__btn--number' @click="tab(0)">0</view>
									</view>
									<view class="content">
										<view class="content__btn--betMax">
											<view class="content__btn_max">
												最大投注
											</view>
											<view class="limit-stake">
												1000
											</view>
										</view>
										<view class="content__btn--delete" @click="delInput" v-if="isClick">
											<view class="delete-icon"></view>
										</view>
										<view class="content__btn--delete" v-else>
											<view class="delete-icon"></view>
										</view>
										<view class="content__btn--confirm">
											<view>确认</view>
										</view>
									</view>
								</view>
							</view>
						</view>
					</scroll-view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				tabs: [
					{
						name: '全场'
					},
					{
						name: '第一局'
					},
					{
						name: '第二局'
					},
					{
						name: ''
					},
					{
						name: ''
					}
				],
				currentTab:0,
				scrollH:500,
				isSelected:false,
				amount: '输入金额',
				direction:true,
				keyboard_active:true,
				isClose:false,
				tabnum:1,
				input_focus:false,
				isClick:false
			}
		},
		methods:{
			change(e) {
				this.currentTab = e.index;
			},
			selected(){
				this.isSelected = !this.isSelected
				console.log(1);
			},
			showKeyboard(){
				this.keyboard_active = !this.keyboard_active
				this.input_focus = !this.input_focus
			},
			close(){
				this.isClose = !this.isClose
			},
			tab(value){
				if(this.tabnum === 1){
					this.amount = ''
				}
				this.direction = false
				this.tabnum++
				this.amount += value
				this.isClick =true
				if(this.amount.length >= 7){
					this.amount = this.amount.substr(0,6);
				}
			},
			delInput(){
				this.amount = [...this.amount.split('')]
				this.amount.pop()
				this.amount = this.amount.join("")
				console.log(this.amount);
				if(this.amount.length === 0){
					this.amount = "输入金额"
					this.direction = true
					this.tabnum = 1
					this.isClick = false
				}
			}
		},
		onLoad(options) {
		  //获取可视区域的高度
		  uni.getSystemInfo({
		    success: (res) => {
		      console.log(res)
		      this.scrollH = res.windowHeight-uni.upx2px(414)
		    }
		  })
		}
	}
</script>

<style lang="less">
	.tipsContent1 {
	  width: 100%;
	  height: 502upx;
	  background-color: #FFFFFF;
	  border-radius: 15upx;
	  display: flex;
	  // justify-content: center;
	  flex-direction: column;
	  align-items: center;
	  position: relative;
	
	  .buttom {
	    display: flex;
	    justify-content: center;
	    align-items: center;
	    color: #666666;
	    font-size: 30upx;
	    padding-bottom: 40upx;
	  }
	}
	
	.betting-info{
		overflow-y: visible;
		width: 100%;
		height: 328rpx;
		display: flex;
		flex-direction: column;
		background: #1d2638;
		position: fixed;
		top: 88rpx;
		/* #ifdef APP-PLUS */
		top: 0;
		/* #endif */
		z-index: 2;
		.info-title{
			padding-left: 20rpx;
			display: flex;
			align-items: center;
			font-size: 24rpx;
			image{
				width: 40rpx;
				height: 40rpx;
			}
			.tournament-name{
				margin-left: 12rpx;
				padding-top: 20rpx;
				padding-bottom: 20rpx;
			}
			.match-round{
				color: #758bb5;
				margin-left: 6rpx;
			}
		}
		.info-team{
			padding-left: 28rpx;
			padding-right: 28rpx;
			display: flex;
			justify-content: center;
			align-items: center;
			align-items: flex-start;
			.team-info{
				width: 216rpx;
				.team-logo{
					width: 144rpx;
					height: 144rpx;
				}
				.team-name{
					width: 100%;
					word-wrap: break-word;
					font-size: 24rpx;
				}
			}
			.betting-status{
				width: calc(100% - 432rpx);
				height: 184rpx;
				display: flex;
				flex-direction: column;
				align-items: center;
				.status-early{
					height: 144px;
					display: flex;
					justify-content: center;
					align-items: center;
					.is-early{
						.match-date{
							font-size: 24rpx;
						}
						.match-time{
							font-size: 32rpx;
							color: #fff;
						}
					}
				}
				.is-raedy{
					font-size: 24rpx;
					color: #2197f4;
				}
			}
		}
	}
	video{
		display: none;
		width: 100%;
		height: 328rpx;
		position: fixed;
		top: 88rpx;
		/* #ifdef APP-PLUS */
		top: 0;
		/* #endif */
		z-index: 2;
		left: 0;
	}
	.scroll{
		position: relative;
		top:414rpx;
	}
	.betting-odds{
		margin-bottom: 8rpx;
		padding: 24rpx 32rpx;
		background: #182032;
		
		.stage-title{
				position: relative;
			    display: flex;
				justify-content: center;
			    font-size: 24rpx;
			    color: #758bb5;
				&::after{
					content: '';
					position: absolute;
					top: 0;
					bottom: 0;
					left: 15.46667vw;
					margin: auto;
					height: 1px;
					width: 23.46667vw;
					background: #27394c;
				}
				&::before{
					content: '';
					position: absolute;
					top: 0;
					bottom: 0;
					right: 15.46667vw;
					margin: auto;
					height: 1px;
					width: 23.46667vw;
					background: #27394c;
				}
		}
		.group-list{
			margin-bottom: 30rpx;
			.odds-group-title{
				margin-top: 16rpx;
				height: 17px;
				display: flex;
				align-items: center;
				font-size: 24rpx;
				text-align: left;
				.empty-badge{
					width: 4rpx;
					height: 18rpx;
					background: #bacef1;
				}
				.title{
					margin: 0 16rpx 0 8rpx;
				}
			}
			.group-odds{
				display: flex;
				flex-wrap: wrap;
				justify-content: space-between;
				.odds-btn{
					width: calc((100% - 43rpx) / 2);
					margin-top: 16rpx;
					display: flex;
					justify-content: center;
					align-items: center;
					height: 80rpx;
					border-radius: 8rpx;
					background: linear-gradient(90deg,#298a97,#317699);
					box-shadow: 0 0 8rpx 0 rgba(14,20,34,.5);
					.button-dark-border{
						background: linear-gradient(#323e57,#1d2639);
						height: 76rpx;
						width: calc(100% - 4rpx);
						border-radius: 6rpx;
						background-color: #252f44;
						.btn-left{
							text-align: left;
							width: calc(100% - 4rpx);
							height: 72rpx;
							display: flex;
							justify-content: space-between;
							align-items: center;
							padding-left: 20rpx;
							padding-right: 20rpx;
							border-radius: 4rpx;
							overflow-wrap: break-word;
							box-sizing: border-box;
							.button-name{
								font-size: 24rpx;
								max-width: 65%;
								overflow-wrap: break-word;
							}
						}
					}
					.btn-selected{
						background: #0585a1;
						color: #fff;
						transition: all .3s ease-out;
					}
				}
				.btn-selected1{
					background: linear-gradient(90deg,#1efffa,#34cdff);
					box-shadow: 0 1px 4px 0 rgba(0,128,255,.3);
				}
			}
		}
		
	}
	.tab-content{
		position: fixed;
		height: 96rpx;
		width: 100%;
		z-index: 2;
		background: #090e16;
		bottom: 0;
		display: flex;
		align-items: center;
		height: 96rpx;
		background-color: #0c121f;
		border-top: 1px solid #125e72;
		.selected-text{
			margin-left: 32rpx;
			display: flex;
			justify-content: center;
			align-items: center;
			font-size: 24rpx;
			color: #fff;
			.selected-number{
				border-radius: 200rpx;
				padding: 2rpx 14rpx;
				background: #526585;
				margin-left: 16rpx;
			}
		}
		.bet-amount{
			margin-left: 32rpx;
			text-align: left;
			font-size: 24rpx;
			color: #fff;
			view{
				.total-return{
					color: #1ee8e7;
					margin-left: 8rpx;
				}
			}
		}
		.toggle-tab{
			margin-left: auto;
			margin-right: 32rpx;
			font-size: 24rpx;
			color: #758bb5;
		}
		.bet-btn{
			    width: 39.73333vw;
			    height: 88rpx;
			    display: flex;
			    justify-content: center;
			    align-items: center;
			    background-image: linear-gradient(135deg,#21aab1,#2e8eb4);
			    box-shadow: 0 0 8rpx 0 rgba(14,20,34,.5), inset 0 2rpx 0 0 hsla(0,0%,100%,.22);
			    border: 2rpx solid #22d8d9;
			    color: #fff;
		}
	}
	
	.bet-slip-pop{
		max-height: calc(100% - 284rpx);
		bottom: 96rpx;
		position: fixed;
		z-index: 2;
		border-radius: 12rpx 12rpx 0 0;
		background: #182032;
		overflow: hidden;
		height: auto;
		transition-property: transform;
		transition-duration: .3s;
		width: 100%;
		left: 0;
		.bet-slip-pop-header{
			width: 100%;
			height: 36px;
			display: flex;
			justify-content: center;
			align-items: center;
			justify-content: flex-end;
			background: #13757e;
			border-radius: 6px 6px 0 0;
			.slip-number{
				border-radius: 200rpx;
				margin-left: 16rpx;
				padding: 2rpx 14rpx;
				color: #fff;
				background: #252f44;
				font-size: 24rpx;
			}
			.remove-all{
				margin-right: auto;
				margin-left: 12rpx;
				font-size: 24rpx;
				color: #fff;
			}
			.pop-header-text{
				display: flex;
				align-items: center;
				margin-right: 32rpx;
				color: #fff;
				font-size: 28rpx;
				.pop-header-balance{
					font-size: 24rpx;
					margin-right: 8rpx;
					color: rgba(240,250,255,.6);
				}
			}
			.pop-header-close{
				background-position: 50%;
				background-repeat: no-repeat;
				width: 44rpx;
				height: 44rpx;
				background-image: url('/static/images/icon22.svg');
				padding: 16rpx;
				border-left: 2rpx solid rgba(156,170,196,.4);
			}
		}
	}
	.close1{
		height: 500rpx;
		transition: all .2s ease-out;
		overflow: hidden;
	}
	.close2{
		height: 0;
		transition: all .2s ease-out;
		overflow: hidden;
	}
	
	.bet-slip-pop-body{
		display: flex;
		flex-direction: column;
		width: 100%;
		max-height: calc(100vh - 700rpx);
		justify-content: center;
		align-items: center;
		.__vuescroll{
			height: unset;
			width: 100%;
			padding: 0px;
			position: relative;
			overflow: hidden;
			.__slide{
				position: relative;
				box-sizing: border-box;
				transform-origin: left top 0px;
				transform: translate3d(0px, 0px, 0px) scale(1);
				height: 450rpx;
				.odds-list{
					display: flex;
					flex-direction: column;
					.odds-item{
						position: relative;
						height: 164rpx;
						display: flex;
						background: #182032;
						border-left: 4rpx solid transparent;
						padding-top: 20rpx;
						padding-bottom: 20rpx;
						padding-right: 16rpx;
						margin-top: 1px;
						box-sizing: border-box;
						.odds-list-line{
							width: calc(100% - 32rpx);
							height: 2rpx;
							margin-top: -22rpx;
							margin-left: 16rpx;
							position: absolute;
							background: #1d2638;
						}
						.remove-odds{
							width: 64rpx;
							display: flex;
							justify-content: center;
							.remove-odds-icon{
								margin-top: 10rpx;
								background-position: 50%;
								background-repeat: no-repeat;
								width: 16rpx;
								height: 16rpx;
								background-image: url('/static/images/icon23.svg');
							}
						}
						.odds-item-match{
							position: relative;
							display: flex;
							flex-direction: column;
							justify-content: space-between;
							text-align: left;
							font-size: 24rpx;
							color: #526585;
							.odds-name{
								color: #FFFFFF;
								font-size: 28rpx;
							}
							
						}
						.odds-item-money{
							display: flex;
							flex-direction: column;
							justify-content: space-between;
							align-items: flex-end;
							margin-left: auto;
							.item-money{
								height: 64rpx;
								display: flex;
								justify-content: center;
								align-items: center;
								.money-odds{
									font-size: 28rpx;
									color: #1ee8e7;
								}
								
								.stake-input{
									width: 144rpx;
									height: 64rpx;
									margin-left: 32rpx;
									display: flex;
									align-items: center;
									justify-content: flex-end;
									background: #151b29;
									border: 1px solid #0c121f;
									border-radius: 4rpx;
									padding-right: 12rpx;
									.input-text{
										border-right: 1px solid transparent;
										border-left: 1px solid transparent;
										color: #bacef1;
										font-size: 24rpx;
									}
									.input-text-focus-right{
										color: #fff;
										font-size: 32rpx;
										border-right: 1px solid transparent;
										animation-name: input-breathing-right;
										animation-duration: 1.2s;
										animation-iteration-count: infinite;
										animation-fill-mode: both;
									}
									.input-text-focus-left{
										color: #bacef1;
										font-size: 24rpx;
										border-left: 1px solid transparent;
										animation-name: input-breathing-left;
										animation-duration: 1.2s;
										animation-iteration-count: infinite;
										animation-fill-mode: both;
									}
									@-webkit-keyframes input-breathing-left{
										0% {
										    border-left: 1px solid #1ee8e7;
										}
										60% {
										    border-left: 1px solid #20304a;
										}
										100% {
										    border-left: 1px solid #1ee8e7;
										}
									}
									@-webkit-keyframes input-breathing-right{
										0% {
										    border-right: 1px solid #1ee8e7;
										}
										60% {
										    border-right: 1px solid #20304a;
										}
										100% {
										    border-right: 1px solid #1ee8e7;
										}
									}
								}
								.stake-input-focus{
									border: 1px solid #125e72;
								}
							}
							.item-return{
								color: #526585;
								font-size: 24rpx;
							}
						}
					}
					
					.keyboard-item-active{
						height: 208rpx;
						transition: all .2s ease-out;
						overflow: hidden;
					}
					.keyboard-item{
						height: 0;
						transition: all .2s ease-out;
						overflow: hidden;
					}
					.bet-keyboard{
						box-sizing: border-box;
						display: flex;
						justify-content: space-between;
						align-items: center;
						flex-direction: column;
						width: 100%;
						height: 208rpx;
						padding: 16rpx 0;
						background: #182032;
						font-size: 16rpx;
						.content{
							display: flex;
							justify-content: space-between;
							align-items: center;
							width: calc(100% - 16rpx);
							color: #fff;
							.content__btn--number{
								width: calc((100% - 54rpx) / 10);
								font-size: 44rpx;
								font-weight: 300;
								height: 84rpx;
								background: #3d475e;
								box-shadow: 0 2rpx 4rpx 0 rgba(9,14,22,.5), inset 0 2rpx 0 0 rgba(95,108,132,.4);
								border-radius: 8rpx;
								display: flex;
								justify-content: center;
								align-items: center;
							}
							.content__btn--betMax{
								flex-direction: column;
								width: calc(30% - 3rpx);
								height: 84rpx;
								background: #3d475e;
								box-shadow: 0 2rpx 4rpx 0 rgba(9,14,22,.5), inset 0 2rpx 0 0 rgba(95,108,132,.4);
								border-radius: 8rpx;
								display: flex;
								justify-content: center;
								align-items: center;
								.content__btn_max{
									font-size: 32rpx;
								}
								.limit-stake{
									font-size: 26rpx;
									line-height: 28rpx;
								}
							}
							.content__btn--delete{
								width: calc((70% - 9rpx) / 2);
								height: 84rpx;
								background: #3d475e;
								box-shadow: 0 2rpx 4rpx 0 rgba(9,14,22,.5), inset 0 2rpx 0 0 rgba(95,108,132,.4);
								border-radius: 8rpx;
								display: flex;
								justify-content: center;
								align-items: center;
								.delete-icon{
									background-image: url('/static/images/icon24.svg');
									background-size: cover;
									background-position: 50%;
									background-repeat: no-repeat;
									width: 70rpx;
									height: 40rpx;
								}
							}
							.content__btn--confirm{
								    width: calc((70% - 9rpx) / 2);
								    background: #515d75;
								    color: #fff;
								    height: 84rpx;
								    background: #3d475e;
								    box-shadow: 0 2rpx 4rpx 0 rgba(9,14,22,.5), inset 0 2rpx 0 0 rgba(95,108,132,.4);
								    border-radius: 8rpx;
								    display: flex;
								    justify-content: center;
								    align-items: center;
									view{
										font-size: 32rpx;
									}
							}
						}
					}
				}
			}
		}
	}
</style>
