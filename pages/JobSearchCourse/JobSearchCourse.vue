<template>
	<scroll-view scroll-y style="width: 100%; height: 100vh;" @scroll="rightScroll">
		<view class="content">
			<image src="../../static/tabBar/homeBg.png" class="imgBg" v-if="!opacityNum"></image>
			<view class="nav-tab" :style="{zIndex:99,position: 'fixed',backgroundColor:opacityNum?'#fff':'',paddingTop:navBarHeight + 'px'}">
				<view class="search-box">
					<image src="../../static/tabBar/search.png" class="icon-search"></image>
					<input type="text" placeholder="搜索课程" placeholder-class="placeholder_14" confirm-type="search"
						:class="['search', focus && 'focus']" :disabled="disabled" @confirm="handleConfirm" />
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
				<course :Data="primaryList[primaryIndex].child[secondIndex].child" v-if="activatIndex == 0"></course>
			</view>
		</view>
	</scroll-view>
</template>

<script>
	import Data from '@/util/data.js'
	import course from '@/components/course/course.vue'
	export default {
		components: {
			course
		},
		data() {
			return {
				tabData: ['找公司', '找岗位'],
				activatIndex: 0,
				bannerList: [{
						img: '../../static/tabBar/bar2bg.png'
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
			this.primaryList = Data.courseData
			this.navBarHeight = uni.getSystemInfoSync().statusBarHeight
		},
		methods: {
			handleConfirm(e) {
				console.log(e);
			},
			rightScroll(e){
				const scrollTop = e.detail.scrollTop;
				var opacity = scrollTop / 150;
				if(opacity >= 1){
					this.opacityNum = 1
				}else{
					this.opacityNum = opacity
				}
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
			height:88rpx;
			display: flex;
			align-items: center;
			justify-content: space-between;

			.search-box {
				margin-left: 32rpx;
				padding-left: 30rpx;
				padding-right: 30rpx;
				border-radius: 10rpx;
				display: flex;
				align-items: center;
				box-sizing: border-box;
				justify-content: left;
				width: 460rpx;
				height: 68rpx;
				background: rgba(255, 255, 255, 0.2);
				border-radius: 34rpx;
				border: 2rpx solid rgba(255, 255, 255, 0.52);
				backdrop-filter: blur(3px);

				.icon-search {
					width: 28rpx;
					height: 28rpx;
				}

				.search {
					flex: 0 0 140rpx;
					font-size: 28rpx;
					margin-left: 12rpx;
					transition: flex .3s;

					&.focus {
						flex: 1 0 80rpx;
					}
				}
			}
		}

		.swiperBox {
			padding-top: 200rpx;
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