<template>
	<view class="course">
		<view class="courseList" v-for="(item,index) in Data" :key="index">
			<view class="imgBox">
				<image :src="item.img" class="img"></image>
				<view class="people">
					<view class="tips">
						{{item.people}}人购买
					</view>
				</view>
			</view>
			<view class="rightInfo">
				<view class="name">
					{{item.name}}
				</view>
				<view class="moneyBox">
					<view class="money">
						¥{{item.money}}
					</view>
					<view class="huaMoney">
						¥{{item.huaMoney}}
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "course",
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
	.course {
		.courseList {
			background: #FFFFFF;
			border-radius: 12rpx;
			padding: 32rpx 28rpx 32rpx 28rpx;
			margin-bottom: 20rpx;
			display: flex;

			.imgBox {
				position: relative;
				margin-right: 24rpx;
				.img{
					width: 220rpx;
					height: 160rpx;
					border-radius: 16rpx;
				}
				.people{
					position: absolute;
					bottom: 7rpx;
					width: 220rpx;
					height: 44rpx;
					background: linear-gradient(90deg, rgba(250,251,253,0) 0%, rgba(0,0,0,0.82) 100%);
					border-radius: 0rpx 0rpx 20rpx 20rpx;
					font-size: 20rpx;
					font-weight: 400;
					text-align: right;
					line-height:44rpx ;
					color: #FFFFFF;
					.tips{
						margin-right: 20rpx;
					}
				}
			}
			.rightInfo{
				width: 100%;
				display: flex;
				flex-direction: column;
				justify-content: space-between;
				.name{
					width: 100%;
					font-size: 32rpx;
					font-weight: 500;
					color: #333333;
					margin-bottom: 20rpx;
					text-overflow: ellipsis;
					display: -webkit-box;
					-webkit-box-orient: vertical;
					-webkit-line-clamp: 2;
					overflow: hidden;
				}
				.moneyBox{
					display: flex;
					align-items: center;
					.money{
						margin-right: 12rpx;
						font-size: 32rpx;
						font-weight: 500;
						color: #5184F1;
					}
					.huaMoney{
						font-size: 20rpx;
						font-weight: 400;
						color: #999999;
						text-decoration-line:line-through;
					}
				}
			}
		}
	}
</style>