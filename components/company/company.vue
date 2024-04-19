<template>
	<view class="company">
		<view class="companyList" v-for="(item,index) in Data" :key="index">
			<view class="companyInfo">
				<image src="../../static/tabBar/companyLogo.png" class="logo"></image>
				<view class="right">
					<view class="companyName">
						{{item.name}}
					</view>
					<view class="cityBox">
						<image src="../../static/tabBar/city.png" class="cityIcon"></image>
						<view class="cityName">
							{{item.city}}
						</view>
					</view>
				</view>
			</view>
			<view class="tipsBox">
				<scroll-view scroll-x scroll-with-animation style="width:auto;overflow:hidden;">
					<view class="tips" v-for="(item1,index1) in item.tips" :key="index1">
						{{item1}}
					</view>
				</scroll-view>
			</view>
			<view class="line">

			</view>
			<view class="postBox">
				<view class="postList" v-for="(item1,index1) in item.postData" :key="index1">
					<view class="money">
						{{item1.money}}
					</view>
					<view class="postName">
						{{item1.name}}
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "company",
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

			.companyInfo {
				display: flex;
				align-items: center;

				.logo {
					width: 92rpx;
					height: 92rpx;
					margin-right: 12rpx;
				}

				.right {
					.companyName {
						font-size: 32rpx;
						font-weight: 500;
						color: #333333;
					}

					.cityBox {
						margin-top: 12rpx;
						display: flex;
						align-items: center;

						.cityIcon {
							width: 24rpx;
							height: 24rpx;
							margin-right: 6rpx;
						}

						.cityName {
							font-size: 26rpx;
							font-weight: 400;
							color: #666666;
						}
					}
				}
			}

			.tipsBox {
				width: 100%;
				white-space: nowrap;
				margin: 32rpx 0;

				.tips {
					display: inline-block;
					margin-right: 12rpx;
					padding: 6rpx 28rpx 6rpx 30rpx;
					background: #F2F5FA;
					border-radius: 6rpx;
					opacity: 0.5;
				}
			}

			.line {
				width: 646rpx;
				height: 2rpx;
				background: #DCE2EB;
				border-radius: 12rpx;
				opacity: 0.2;
				margin-bottom: 32rpx;
			}

			.postBox {
				display: flex;
				align-items: center;
				justify-content: space-around;

				.postList {
					display: flex;
					flex-direction: column;
					align-items: center;

					.money {
						font-size: 24rpx;
						font-weight: 500;
						color: #5184F1;
						margin-bottom: 8rpx;
					}

					.postName {
						width: 176rpx;
						text-align: center;
						font-size: 22rpx;
						font-weight: 400;
						color: #666666;
						white-space: nowrap;
						overflow: hidden;
						text-overflow: ellipsis;
					}
				}
			}
		}
	}
</style>