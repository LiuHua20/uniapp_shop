<template>
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
</template>

<script>
	export default {
		props: ['goods'],
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
				    ]
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
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
</style>