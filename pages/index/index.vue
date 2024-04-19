<template>
	<scroll-view scroll-y style="width: 100%; height: 100vh;" @scroll="rightScroll">
		<view class="content">
			<image src="../../static/tabBar/homeBg.png" class="imgBg" v-if="!opacityNum"></image>
			<view class="nav-tab" :style="{zIndex:99,position: 'fixed',backgroundColor:opacityNum?'#fff':'',paddingTop:navBarHeight + 'px'}">
				<image src="../../static/tabBar/search.png" class="nav-left" @click="search"></image>
				<view class="nav-centent">
					<view class="nav-name" v-for="(item,index) in tabData" :key="index" @click="tabSwitcHover(index)">
						<view class="nav-name-item" :class="activatIndex == index?'nav-name-activate':'nav-name-item'">
							{{item}}
						</view>
						<view class="line" :style="{opacity:activatIndex == index?'1':'0'}">
						</view>
					</view>
				</view>
				<view class="right">
				</view>
			</view>
			<view class="swiperBox" :style="{paddingTop: (navBarHeight * 2) + 90 + 'rpx'}">
				<swiper :autoplay="true" :interval="3000" :duration="1000" style="width: 702rpx;height: 280rpx;">
					<swiper-item v-for="(item,index) in bannerList" :key="index">
						<image :src="item.img" class="swiper-item"></image>
					</swiper-item>
				</swiper>
			</view>
			<view class="topNav" :style="{top:(navBarHeight * 2) + 70 + 'rpx'}">
				<view class="scroll-view_x">
					<scroll-view scroll-x scroll-with-animation style="width:auto;overflow:hidden;    height:60rpx;">
						<view class="primaryClass" v-for="(item,index) in primaryList" :key="index"
							@click="primarySwitcHover(item,index)">
							<view :class="primaryIndex==index?'primaryNameActiva':'primaryName'">
								{{item.name}}
							</view>
							<image src="../../static/tabBar/icon.png" class="lines" v-if="primaryIndex==index"></image>
						</view>
					</scroll-view>
				</view>
				<view class="scroll-view_x1">
					<scroll-view scroll-x scroll-with-animation style="width:auto;overflow:hidden;">
						<view class="secondLevel" v-for="(item,index) in primaryList[primaryIndex].child" :key="index"
							@click="secondSwitcHover(item,index)">
							<view :class="secondIndex==index?'secondNameActiva':'secondName'">
								{{item.name}}
							</view>
						</view>
					</scroll-view>
				</view>
			</view>
			<view class="centent">
				<uni-load-more status="asd" v-if="loading"></uni-load-more>
				<company :Data="primaryList[primaryIndex].child[secondIndex].child" v-if="activatIndex == 0"></company>
				<position :Data="primaryList[primaryIndex].child[secondIndex].child" v-else></position>
			</view>
		</view>
	</scroll-view>
</template>

<script>
	import Data from '@/util/data.js'
	import company from '@/components/company/company.vue'
	import position from '@/components/position/position.vue'
	export default {
		components: {
			company,
			position
		},
		data() {
			return {
				tabData: ['找公司', '找岗位'],
				activatIndex: 0,
				bannerList: [{
						img: '../../static/tabBar/banner1.png'
					},
					{
						img: '../../static/tabBar/banner2.png'
					}
				],
				primaryList: [],
				// 一级索引
				primaryIndex: 0,
				// 二级索引
				secondIndex: 0,
				loading: true,
				opacityNum: 0,
				navBarHeight:''
			}
		},
		onLoad() {
			this.primaryList = Data.primaryList
			this.navBarHeight = uni.getSystemInfoSync().statusBarHeight
		},
		methods: {
			search() {},
			rightScroll(e) {
				const scrollTop = e.detail.scrollTop;
				var opacity = scrollTop / 150;
				if (opacity >= 1) {
					this.opacityNum = 1
				} else {
					this.opacityNum = opacity
				}
			},
			tabSwitcHover(index) {
				this.activatIndex = index
				if (index == 0)
					this.primaryList = Data.primaryList
				else
					this.primaryList = Data.position
			},
			primarySwitcHover(item, index) {
				this.primaryIndex = index
			},
			secondSwitcHover(item, index) {
				this.secondIndex = index
			}
		}
	}
</script>

<style lang="scss" scoped>
	.content {
		min-height: 100vh;
		background-color: #F2F5FA;

		.imgBg {
			position: fixed;
			z-index: 4;
			top: 0;
			width: 750rpx;
			height: 440rpx;
		}

		.nav-tab {
			width: 100%;
			position: fixed;
			z-index: 9;
			height: 88rpx;
			display: flex;
			align-items: center;
			justify-content: space-between;

			.nav-left {
				margin-left: 30rpx;
				width: 35rpx;
				height: 35rpx;
			}

			.nav-centent {
				display: flex;
				align-items: center;

				.nav-name {
					margin-right: 30rpx;
					display: flex;
					flex-direction: column;
					align-items: center;

					.nav-name-item {
						font-weight: 400;
						color: #999999;
						font-size: 28rpx;
					}

					.nav-name-activate {
						font-weight: 600;
						color: #333333;
						font-size: 32rpx;
					}

					.line {
						width: 40rpx;
						height: 8rpx;
						margin-top: 10rpx;
						border-radius: 20rpx;
						background-color: rgb(81, 132, 241);
					}
				}
			}

			.right {
				width: 80rpx;
			}
		}

		.swiperBox {
			margin: 0 24rpx;
			position: relative;
			z-index: 8;

			.swiper-item {
				width: 100%;
				height: 100%;
			}
		}

		.topNav {
			position: sticky;
			z-index: 9;
			padding: 10rpx 0;
			background-color: #F2F5FA;
		}

		.scroll-view_x {
			width: 92%;
			white-space: nowrap;
			margin: 32rpx 24rpx 26rpx 24rpx;

			/deep/ .uni-scroll-view-content {
				display: flex;
			}

			.primaryClass {
				margin-right: 40rpx;
				display: inline-block;
				position: relative;

				.primaryName {
					font-size: 28rpx;
					font-weight: 400;
					color: #999999;
				}

				.primaryNameActiva {
					font-size: 28rpx;
					font-weight: 600;
					color: #333333;
				}

				.lines {
					position: absolute;
					z-index: 10;
					width: 100%;
					bottom: 2rpx;
					height: 12rpx;
				}
			}
		}

		.scroll-view_x1 {
			width: 92%;
			white-space: nowrap;
			margin: 0 24rpx 24rpx 24rpx;

			/deep/ .uni-scroll-view-content {
				display: flex;
			}

			.secondLevel {
				display: inline-block;
				margin-right: 20rpx;
				padding: 0 20rpx;
				max-height: 60rpx;
				line-height: 60rpx;
				background-color: #fff;
				border-radius: 6rpx;
				box-sizing: border-box;

				.secondName {
					color: #999999;
					font-size: 26rpx;
				}

				.secondNameActiva {
					color: #5184F1;
					font-size: 28rpx;
				}
			}
		}

		.centent {
			padding: 0 24rpx;
		}

	}
</style>