<template>
	<view>
		<!--用于占位，避免自定义导航栏覆盖页面内容  -->
		<view class="standView"></view>
		<!-- 自定义navbar -->
		<u-navbar :is-fixed="true" :is-Back="true" left-text="返回" title="订单" :bgColor="bgColor">
		</u-navbar>
		<!-- 搜索框 -->
		<u-search :show-action="true" actionText="搜索" :animation="true" placeholder="在此输入您的订单" v-model="keyword"
			:bgColor="sColor">
		</u-search>
		<!-- 导航栏 -->
		<view class="bar">
			<u-button>全部</u-button>
			<u-button>待支付</u-button>
			<u-button>发货</u-button>
			<u-button>售后</u-button>
		</view>
		<!-- 正文内容 -->
		<view class="container">
			<scroll-view scroll-y style="height: 100%;width: 100%;" enable-back-to-top>
				<view class="content">
					<view v-for="(item,index) in dataList" :key="index">
						<view class="item">
							<view class="item-top">
								<view class="item-top-left">
									{{msgType}}
								</view>
								<view class="item-top-right">
									•••
								</view>
							</view>

							<view class="item-content">

								<view class="item-content-item">
									<view class="item-content-item-left">跟团号:</view>
									<view class="item-content-item-right">
										{{item.num}}
									</view>
								</view>
								<view class="item-content-item">
									<view class="item-content-item-left">支付时间:</view>
									<view class="item-content-item-right">
										{{item.PayTime}}
									</view>
								</view>
								<view class="item-content-item">
									<view class="item-content-item-left">团长名:</view>
									<view class="item-content-item-right">
										{{item.MerName}}
									</view>
								</view>
								<view class="item-content-goods">
									<view v-for="(y, index) in item.goods" :key="index">
										<view class="item-content-goods-image">
											<image :src="y.img" mode="" class="img"></image>
										</view>
										<view class="item-content-goods-name">{{y.name}}</view>
									</view>

									<view class="item-total">
										<view class="item-total-price">￥ {{item.TotalPrice}}</view>
										<view class="item-total-count">共 {{item.count}} 件</view>
									</view>
								</view>
							</view>
							<view class="item-btn">
								<view class="item-btn-left">查看详情</view>
								<u-icon name="arrow-right" class="item-btn-right"></u-icon>
							</view>
						</view>
					</view>
				</view>
				<u-loadmore :status="loadStatus[0]" bgColor="#f2f2f2">
				</u-loadmore>
			</scroll-view>

		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				bgColor: '#f2fdff',
				sColor: '#ffffff',
				keyword: '',
				/* current: 0,
				swiperCurrent: 0,
				totalPages: 0, */
				dataList: [{
					num: 80,
					PayTime: '2022-06-20',
					MerName: '饼家',
					TotalPrice: 9.8,
					count: 1,
					goods: [{
						name: '鸡蛋灌饼',
						img: require('@/static/item.png'),
					}],
				}, {
					num: 80,
					PayTime: '2022-06-20',
					MerName: '饼家',
					TotalPrice: 19.6,
					count: 2,
					goods: [{
							name: '鸡蛋灌饼',
							img: require('@/static/item.png'),
						},
						{
							name: '鸡蛋灌饼',
							img: require('@/static/item.png'),
						}
					],
				}],
				loadStatus: ['loadmore', 'loadmore', 'loadmore'],
				msgType: "一起购团购平台--销售订单",
			}
		},

		onLoad() {
			//	this.getOrderList()
		},

		methods: {
			/* goback() {
				uni.reLaunch({
					url: 'pages/index/index'
				});
			},
 */

			// 查看详情
			/* showItem(item){
				const aguid = item.aguid
				console.log(aguid)
				const option = {aguid}
				this.$u.route('/pages/Detail/Detail',option)
			} */
		}
	}
</script>

<style>
	/* #ifndef H5 */
	page {
		height: 100%;
		background-color: #f2f2f2;
	}

	/* #endif */
</style>

<style lang="scss" scoped>
	.standView {
		width: 100%;
		height: 100rpx;
		/*  此处高度需要修改 */
		/* background-color: black; */
	}

	.bar {
		width: 90%;
		display: flex;
		flex-direction: row;
		margin-left: 5%;
		margin-top: 18rpx;
	}

	.container {
		display: flex;
		flex-direction: column;
		height: calc(100vh - var(--window-top));
		width: 100%;

		.content {
			flex: 1;

			.item {
				height: 650rpx;
				margin-left: 49rpx;
				margin-top: 15rpx;
				margin-right: 49rpx;
				border-radius: 20rpx;
				background-color: #FFFF;

				.item-top {
					padding-left: 52rpx;
					padding-right: 52rpx;
					padding-top: 40rpx;
					display: flex;
					justify-content: space-between;
					align-items: center;
					border-bottom: 1rpx solid #e8e8e8;

					.item-top-left {
						font-size: 36rpx;
						margin-top: -25rpx;
					}

					.item-top-right {
						font-size: 36rpx;
					}
				}

				.item-content {
					height: 450rpx;
					border-bottom: 1rpx solid #e8e8e8;
					background-color: #FFFFFF;

					.item-content-item {
						color: #777777;
						padding-left: 52rpx;
						padding-top: 20rpx;
						font-size: 30rpx;
						display: flex;
						flex-direction: row;

						.item-content-item-left {
							color: #8b8b8b;
							padding-right: 35rpx;
						}

						.item-content-item-right {
							color: #1b286e;
						}
					}

				}

				.item-content-goods {
					padding-left: 32rpx;
					padding-top: 20rpx;
					margin-top: 30rpx;
					height: 180rpx;
					display: flex;
					flex-direction: row;

					.item-content-goods-image {
						height: 120rpx;
						width: 120rpx;
						margin-left: 25rpx;

						.img {
							height: 120rpx;
							width: 120rpx;
						}
					}

					.item-content-goods-name {
						width: 120rpx;
						color: #777777;
						font-size: 28rpx;
						margin-left: 25rpx;
					}
					
					.item-total {
						height: 100rpx;
						width: 100rpx;
						font-size: 28rpx;
						margin-top: 30rpx;
						position: absolute;
						right: 100rpx;
					}
				}

				.item-btn {
					height: 60rpx;
					font-size: 36rpx;
					padding-top: 20rpx;
					padding-left: 52rpx;
					background-color: #FFFFFF;
					display: flex;
					justify-content: space-between;
					align-items: center;

					.item-btn-right {
						margin-right: 50rpx;
						color: #e8e8e8;
					}
				}
			}
		}
	}
</style>
