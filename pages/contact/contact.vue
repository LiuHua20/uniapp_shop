<template>
	<view>
		<view class="contact">
			<image class="img" src="http://www.itcast.cn/2018czydz/images/gywmban.jpg"></image>
			<view class="info">
				<view @click="Rikka">小鸟游六花：身体娇小的重度中二病患者。</view>
				<view>地址：就读于私立银杏学园。</view>
			</view>
		</view>
		<map class="map" :longitude="longitude" :scale="scale" :latitude="latitude" :markers="markers"></map>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				longitude: 108.19873,
				latitude: 23.543773,
				scale: 11,
				markers: [
					{
						longitude: 108.19873,
						latitude: 23.543773,
						iconPath: '../../static/1.jpg',
						width: 30,
						height: 30
					}
				]
			}
		},
		methods: {
			Rikka(){
				alert("   有着紫色的呆毛，右眼用眼罩遮盖，左手用绷带绑住，有用隐形眼镜制造的异色瞳，贫乳属性。自称自己的右眼是邪王真眼，拥有看到异世界“不可视境界线”的能力。厌恶西红柿圣女果番茄。");
				// 弹出拨打电话用法
				// uni.makePhoneCall({
				// 	phoneNumber: "123-456-7890"
				// })
			}
		}
	}
</script>

<style lang="scss">
	.img{
		width: 750rpx;
		height: 320rpx;
	}
	
	.info{
		padding: 10rpx 20rpx;
		font-size: 30rpx;
		view{
			line-height: 80rpx;
			border-bottom: 1rpx solid #eee;
		}
	}
	
	.map{
		width: 750rpx;
		height: 750rpx;
	}
</style>
