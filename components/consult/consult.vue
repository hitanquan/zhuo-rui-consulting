<template>
	<view class="company">
		<view class="companyList" v-for="(item,index) in Data" :key="index">
			<view class="userBox">
				<view class="userLeft">
					<view class="name">
						{{item.name}}
					</view>
					<view class="type">
						{{item.type}}
					</view>
				</view>
				<view class="rightBox">
					<view class="tips">
						评分
					</view>
					<view class="mark">
						{{item.mark}}
					</view>
				</view>
			</view>
			<view class="good">
				<view class="goodTips">擅长:</view>
				<view class="goodInfo">{{item.good}}</view>
			</view>
			<view class="info">
				<view class="infoText">
					{{item.info}}
				</view>
			</view>
			<view class="bottomBox">
				<view class="money">
					{{item.money}}
				</view>
				<view class="bottomRight">
					<view class="people">
						<text class="spen">已咨询</text> {{item.people}}人
					</view>
					<view class="online">
						在线咨询
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "position",
		props: {
			Data: {
				type: Array,
				default: [],
			}
		},
		data() {
			return {

			};
		}
	}
</script>

<style lang="scss" scoped>
	.company {
		.companyList {
			background: #FFFFFF;
			border-radius: 12rpx;
			padding: 28rpx 28rpx 40rpx 28rpx;
			margin-bottom: 20rpx;

			.userBox {
				display: flex;
				align-items: center;
				justify-content: space-between;

				.userLeft {
					display: flex;
					align-items: center;

					.name {
						font-size: 36rpx;
						font-weight: 600;
						color: #333333;
					}

					.type {
						width: 100rpx;
						padding: 6rpx 0;
						background: #5184F1;
						border-radius: 6rpx;
						font-size: 20rpx;
						text-align: center;
						font-weight: 400;
						margin-left: 24rpx;
						color: #FFFFFF;
					}
				}

				.rightBox {
					display: flex;
					align-items: center;

					.tips {
						font-size: 28rpx;
						font-weight: 400;
						color: #999999;
					}

					.mark {
						font-size: 28rpx;
						color: #5184F1;
						margin-left: 12rpx;
					}
				}
			}

			.good {
				width: 100%;
				display: flex;
				margin: 20rpx 0 24rpx 0;

				.goodTips {
					color: #666666;
					font-size: 24rpx;
					margin-right: 10rpx;
				}

				.goodInfo {
					width: 90%;
					color: #999;
					font-size: 24rpx;
				}
			}

			.info {
				padding: 24rpx;
				background: #F2F5FA;
				opacity: 0.4;
				margin-bottom: 28rpx;
				.infoText{
					text-overflow: ellipsis;
					display: -webkit-box;
					-webkit-box-orient: vertical;
					-webkit-line-clamp: 4;
					overflow: hidden;
				}
			}

			.bottomBox {
				display: flex;
				align-items: center;
				justify-content: space-between;

				.money {
					font-size: 32rpx;
					font-weight: 500;
					color: #5184F1;
				}

				.bottomRight {
					display: flex;
					align-items: center;

					.people {
						font-size: 22rpx;
						color: #5184F1;

						.spen {
							padding-right: 5rpx;
							color: #999;
						}
					}
					.online{
						width: 160rpx;
						height: 52rpx;
						background: #5184F1;
						border-radius: 26rpx;
						font-size: 28rpx;
						font-weight: 400;
						line-height: 52rpx;
						text-align: center;
						margin-left: 24rpx;
						color: #FFFFFF;
					}
				}
			}
		}
	}
</style>