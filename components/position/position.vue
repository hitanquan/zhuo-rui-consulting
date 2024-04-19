<template>
	<view class="company">
		<view class="companyList" v-for="(item,index) in Data" :key="index">
			<view class="positionBox">
				<view class="positionName">
					{{item.name}}
				</view>
				<view class="money">
					{{item.money}}
				</view>
			</view>
			<view class="tipsBox">
				<scroll-view scroll-x scroll-with-animation style="width:auto;overflow:hidden;">
					<view class="tips" v-for="(item1,index1) in item.tips" :key="index1">
						{{item1}}
					</view>
				</scroll-view>
			</view>
			<view class="companyBox">
				<view class="company">
					{{item.company}}
				</view>
				<view class="cityBox">
					<image src="../../static/tabBar/city.png" class="cityIcon"></image>
					<view class="cityName">
						{{item.city}}
					</view>
				</view>
			</view>
			<view class="line">

			</view>
			<view class="userInfo">
				<view class="userBox">
					<image :src="item.logo" class="userLogo"></image>
					<view class="userRigth">
						<view class="userName">
							{{item.userName}}
						</view>
						<view class="type">
							{{item.type}}
						</view>
					</view>
				</view>
				<view class="rightBox">
					<view class="iconBox">
						<image src="../../static/tabBar/simple.png" class="icon"></image>
						<view class="iconName">
							投递简历
						</view>
					</view>
					<view class="iconBox">
						<image src="../../static/tabBar/relation.png" class="icon"></image>
						<view class="iconName">
							在线提问
						</view>
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

			.positionBox {
				display: flex;
				align-items: center;
				justify-content: space-between;

				.positionName {
					font-size: 36rpx;
					font-weight: 500;
					color: #333333;
				}

				.money {
					font-size: 36rpx;
					font-weight: 500;
					color: #5184F1;
				}
			}

			.tipsBox {
				width: 100%;
				white-space: nowrap;
				margin: 24rpx 0 20rpx 0;

				.tips {
					display: inline-block;
					margin-right: 12rpx;
					padding: 6rpx 28rpx 6rpx 30rpx;
					background: #F2F5FA;
					border-radius: 6rpx;
					opacity: 0.5;
				}
			}

			.companyBox {
				display: flex;
				align-items: center;
				justify-content: space-between;
				font-size: 24rpx;
				font-weight: 400;
				color: #666666;

				.cityBox {
					margin-top: 12rpx;
					display: flex;
					align-items: center;


					.cityIcon {
						width: 24rpx;
						height: 24rpx;
						margin-right: 4rpx;
					}

					.cityName {
						font-weight: 400;
					}
				}
			}

			.line {
				width: 646rpx;
				height: 2rpx;
				background: #DCE2EB;
				border-radius: 12rpx;
				opacity: 0.2;
				margin: 32rpx 0;
			}

			.userInfo {
				display: flex;
				align-items: center;
				justify-content: space-between;

				.userBox {
					display: flex;
					align-items: center;

					.userLogo {
						width: 60rpx;
						height: 60rpx;
						margin-right: 8rpx;
					}

					.userRigth {
						display: flex;
						flex-direction: column;

						.userName {
							margin-bottom: 4rpx;
							font-size: 24rpx;
							font-weight: 500;
							color: #333333;
						}

						.type {
							font-size: 24rpx;
							font-weight: 400;
							color: #999999;
						}
					}
				}

				.rightBox {
					display: flex;
					align-items: center;

					.iconBox {
						display: flex;
						align-items: center;
						flex-direction: column;
						margin-left: 42rpx;

						.icon {
							width: 22rpx;
							height: 24rpx;
							margin-bottom: 8rpx;
						}
						.iconName{
							font-size: 22rpx;
							font-weight: 400;
							color: #5184F1;
						}
					}
				}
			}


		}
	}
</style>