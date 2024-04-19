<template>
	<scroll-view scroll-y style="width: 100%; height: 100vh;">
		<view class="centent">
			<image src="../../static/tabBar/mineBg.png" class="mineBg"></image>
			<view class="bgBox">
				<view class="userInfo">
					<view class="nav-left">
						<image src="../../static/tabBar/userLogo.png" class="userLogo"></image>
						<view class="userData">
							<view class="phone">
								133****6297
							</view>
							<view class="time">
								注册时间：2024-01-02 17:31:04
							</view>
						</view>
					</view>
					<image src="../../static/tabBar/setting.png" class="setting"></image>
				</view>
				<view class="tabBox">
					<view class="tabList" v-for="(item,index) in tabData" :key="indx">
						<image :src="item.icon" class="icon"></image>
						<view class="iconName">
							{{item.name}}
						</view>
					</view>
				</view>
			</view>
			<view class="moreBox">
				<scroll-view class="scroll" scroll-y scroll-with-animation style="width:auto;overflow:hidden;">
					<view class="moreList" v-for="(item,index) in moreList" :key="index">
						<view class="leftBox">
							<image :src="item.icon" class="moreIcon"></image>
							<view class="moreName">
								{{item.name}}
							</view>
						</view>
						<image src="../../static/tabBar/rightArrow.png" class="rightArrow"></image>
					</view>
				</scroll-view>
			</view>
		</view>
	</scroll-view>
</template>

<script>
	export default {
		data() {
			return {
				tabData: [{
						icon: '../../static/tabBar/icon4.png',
						name: '钱包'
					},
					{
						icon: '../../static/tabBar/icon1.png',
						name: '银行卡'
					},
					{
						icon: '../../static/tabBar/icon2.png',
						name: '实名'
					},
					{
						icon: '../../static/tabBar/icon3.png',
						name: '收藏夹'
					}
				],
				moreList: [{
						icon: '../../static/tabBar/icon-1.png',
						name: '我是求职者'
					},
					{
						icon: '../../static/tabBar/icon-2.png',
						name: '我是企业HR'
					},
					{
						icon: '../../static/tabBar/icon-3.png',
						name: '我是咨询师'
					},
					{
						icon: '../../static/tabBar/icon-4.png',
						name: '我是讲师'
					},
					{
						icon: '../../static/tabBar/icon-5.png',
						name: '我的推广'
					},
					{
						icon: '../../static/tabBar/icon-6.png',
						name: '成为会员'
					},
					{
						icon: '../../static/tabBar/icon-7.png',
						name: '联系客服'
					},
					{
						icon: '../../static/tabBar/icon-8.png',
						name: '关于我们'
					}
				]
			};
		}
	}
</script>

<style lang="scss" scoped>
	page {
		width: 100%;
	}

	.centent {
		width: 100%;
		overflow-x: hidden;
		background: #FFFFFF;
		position: relative;

		.mineBg {
			width: 101%;
			height: 564rpx;
		}

		.bgBox {
			width: 100%;
			position: absolute;
			top: calc(var(--status-bar-height) + 110rpx);

			.userInfo {
				display: flex;
				align-items: center;
				margin: 0 70rpx 0 40rpx;
				justify-content: space-between;

				.nav-left {
					display: flex;
					align-items: center;

					.userLogo {
						width: 124rpx;
						height: 124rpx;
						margin-right: 24rpx;
						border-radius: 50%;
					}

					.userData {
						font-weight: 500;
						color: #FFFFFF;

						.phone {
							font-size: 36rpx;
						}

						.time {
							margin-top: 6rpx;
							font-size: 20rpx;
						}
					}
				}

				.setting {
					width: 44rpx;
					height: 44rpx;
				}
			}

			.tabBox {
				margin: 58rpx 30rpx 0 30rpx;
				display: flex;
				justify-content: space-around;

				.tabList {
					text-align: center;

					.icon {
						width: 44rpx;
						height: 44rpx;
					}

					.iconName {
						font-size: 24rpx;
						font-weight: 400;
						color: #fff;
						margin-top: 12rpx;
					}
				}
			}
		}

		.moreBox {
			padding: 24rpx 40rpx 0 40rpx;
			margin-top: -76rpx;
			z-index: 16;
			position: relative;
			border-radius: 24rpx;
			background: #fff;

			.scroll {
				height: calc(100vh + (var(--status-bar-height) - 564rpx));

			}

			.moreList {
				display: flex;
				align-items: center;
				justify-content: space-between;
				padding: 32rpx 0;
				border-bottom: 2rpx solid rgba(153, 153, 153, .09);

				.leftBox {
					display: flex;
					align-items: center;

					.moreIcon {
						width: 36rpx;
						height: 36rpx;
						margin-right: 20rpx;
					}

					.moreName {
						font-size: 32rpx;
						font-weight: 400;
						color: #333333;
					}
				}

				.rightArrow {
					width: 24rpx;
					height: 24rpx;
				}
			}
		}
	}
</style>