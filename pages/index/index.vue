<template>
	<view class="home">
		<swiper indicator-dots circular>
			<swiper-item v-for="item in swipers" :key="item.id">
				<image :src="item.img"></image>
			</swiper-item>
		</swiper>
		<!-- 导航区域 -->
		<view class="nav">
			<view class="nav_item">
				<view class="iconfont icon-ziyuan"></view>
				<text>黑马超市</text>
			</view>
			<view class="nav_item">
				<view class="iconfont icon-guanyuwomen"></view>
				<text>联系我们</text>
			</view>
			<view class="nav_item">
				<view class="iconfont icon-tupian"></view>
				<text>社区图片</text>
			</view>
			<view class="nav_item">
				<view class="iconfont icon-shipin"></view>
				<text>学习视频</text>
			</view>
		</view>
		
		<!-- 推荐商品 -->
		<view class="hot_goods">
		  <view class="tit">推荐商品</view>
		  <view class="goods_list">
			<view class="goods_item" v-for="(item, index) in goods" :key="item.id">
			  <!-- 确保每个商品显示一个图片，并且按顺序 -->
			  <image :src="imageUrls[index % imageUrls.length]" mode=""></image>
			  <view class="price">
				<text>￥{{item.sell_price}}</text>
				<text>￥{{item.market_price}}</text>
			  </view>
			  <view class="name">
				{{ item.title }}
			  </view>
			</view>
		  </view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				imageUrls: [
				      'https://www.liuhua.wiki/wp-content/uploads/2023/12/1.png',
					  'https://www.liuhua.wiki/wp-content/uploads/2023/12/2.jpg',
					  'https://www.liuhua.wiki/wp-content/uploads/2023/12/3.jpg',
					  'https://www.liuhua.wiki/wp-content/uploads/2023/12/4-scaled.jpg',
					  'https://www.liuhua.wiki/wp-content/uploads/2023/12/5.jpg',
					  'https://www.liuhua.wiki/wp-content/uploads/2023/12/6.jpg',
					  'https://www.liuhua.wiki/wp-content/uploads/2023/12/atri.png',
					  'https://www.liuhua.wiki/wp-content/uploads/2023/12/BA.jpg',
					  'https://www.liuhua.wiki/wp-content/uploads/2023/12/fenmao-scaled.jpg',
					  'https://www.liuhua.wiki/wp-content/uploads/2023/12/preview.jpg'
				    ],
				swipers: [],
				goods: []
			}
		},
		onLoad() {
			this.getSwipers()
			this.gethotGoods()
		},
		methods: {
			// 获取轮播图
			async getSwipers(){
				const res = await this.$myRequest({
					url: '/api/getlunbo'
				})
				// console.log(res);
				this.swipers = res.data.message
			},
			
			// 获取热门商品
			async gethotGoods(){
				const res = await this.$myRequest({
					url: '/api/getgoods?pageindex=1'
				})
				this.goods = res.data.message
			}
		}
	}
</script>

<style lang="scss">
	.home{
		swiper{
			width: 750rpx;
			height: 380rpx;
			image{
				height: 100%;
				width: 100%;
			}
		}	
		.nav{
			display: flex;
			.nav_item{
				width: 25%;
				text-align: center;
				view{
					width: 120rpx;
					height: 120rpx;
					background-color: #b50e03;
					border-radius: 60rpx;
					margin: 10rpx auto;
					line-height: 120rpx;
					color: #fff;
					font-size: 50rpx;
				}
				.icon-tupian{
					font-size: 45rpx;
				}
				text{
					font-size: 30rpx;
				}
			}
		}
		
		.hot_goods {
			background: #eee;
			overflow: hidden;
			margin-top: 10px;
			.tit{
				height: 50px;
				line-height: 50px;
				color: $shop-color;
				text-align: center;
				letter-spacing: 20px;
				background: #fff;
				margin: 7rpx 0;
			}
		
			.goods_list{
				padding: 0 15rpx;
				display: flex;
				flex-wrap: wrap;
				justify-content: space-between;
				.goods_item{
					background-color: #fff;
					width: 355rpx;
					margin: 10rpx 0;
					padding: 15rpx;
					box-sizing: border-box;
					image{
						width: 80%;
						height: 150rpx;
						display: block;
						margin: auto;
					}
					
					.price{
						color: $shop-color;
						font-size: 36rpx;
						text:nth-child(2){
							color: #ccc;
							font-size: 28rpx;
							margin-left: 17rpx;
							text-decoration: line-through;
						}
					}
					
					.name{
						font-size: 28rpx;
						line-height: 50rpx;
						padding-bottom: 15rpx;
						padding-top: 10rpx;
					}
				}
			}
		}
	}
</style>
