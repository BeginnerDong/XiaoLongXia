<template>
	<view>
		<view class="index_topBj mglr4">
			<view class="banner-box">
				<view class="banner oh">
					<swiper class="swiper-box" indicator-dots="true" autoplay="true" interval="3000" duration="1000"  indicator-active-color="#434343">
						<block v-for="(item,index) in labelData" :key="index">
							<swiper-item class="swiper-item">
								<image :src="item" class="slide-image"/>
							</swiper-item>
						</block>
					</swiper>
				</view>
			</view>
		</view>
		
		<view class="indHome">
			<view class="item" @click="Router.navigateTo({route:{path:'/pages/HappyParty/HappyParty'}})">
				<image src="../../static/images/home-icon.png"></image>
				<view class="font13 tit">预约</view>
				<view class="color3 font11 tex2">预约留座</view>
			</view>
			<view class="item"  @click="Router.navigateTo({route:{path:'/pages/luckDraw/luckDraw'}})">
				<image src="../../static/images/home-icon1.png"></image>
				<view class="font13 tit">抽奖</view>
				<view class="color3 font11 tex2">100%中奖</view>
			</view>
			<view class="item" @click="Router.navigateTo({route:{path:'/pages/setCard/setCard'}})">
				<image src="../../static/images/home-icon2.png"></image>
				<view class="font13 tit">集点</view>
				<view class="color3 font11 tex2">免费披萨</view>
			</view>
			<view class="item" @click="Router.navigateTo({route:{path:'/pages/shop/shop'}})">
				<image src="../../static/images/home-icon3.png"></image>
				<view class="font13 tit">商城</view>
				<view class="color3 font11 tex2">积分商城</view>
			</view>
		</view>
		
		<view class="f5H5"></view>
		<view class="pdlr4 inde_TwoPic">
			<view class="flexRowBetween">
				<view class="item" @click="Router.navigateTo({route:{path:'/pages/desktop_scan/desktop_scan'}})"> 
					<image src="../../static/images/home-img.png" mode=""></image>
					<view class="textbox">
						<view class="tit">店内用餐</view>
						<view class="tex">扫桌面二维码</view>
					</view>
				</view>
				<view class="item" @click="Router.navigateTo({route:{path:'/pages/store/store'}})">
					<image src="../../static/images/home-img.png" mode=""></image>
					<view class="textbox">
						<view class="tit">打包自提</view>
						<view class="tex">到店取餐不排队</view>
					</view>
				</view>
			</view>
		</view>
		
		<view class="f5H5"></view>
		<view class="pdlr4 inde_TwoPic">
			<image style="width: 100%;height: 400rpx;" src="../../static/images/choujiang-img.png" mode=""></image>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				Router:this.$Router,
				showView: false,
				score:'',
				wx_info:{},
				scrollTop: 100,
				index: 0,
				text:"1233",
				labelData: [
					"../../static/images/home-banner.png",
					"../../static/images/home-banner.png",
				],
				indProDate:[{},{},{},{}]
			}
		},
		
		onLoad(options) {
			const self = this;
			// self.$Utils.loadAll(['getMainData'], self);
		},
		methods: {
			getMainData() {
				const self = this;
				console.log('852369')
				const postData = {};
				postData.tokenFuncName = 'getProjectToken';
				self.$apis.orderGet(postData, callback);
			}
		},
	};
</script>

<style>

	.index_topBj{padding-top: 30rpx;}
	.swiper-box {height: 330rpx;box-sizing: border-box;overflow: hidden;border-radius: 10rpx;}
	.swiper-box swiper-item {width: 100%;}
	.swiper-box image {width: 100%;height: 100%;}
	
	/* 分类导航 */
	.indHome{ padding: 0 4%;display: flex; justify-content: space-between; align-items: center; flex-wrap:wrap;}
	.indHome .item{width: 25%;text-align: center;padding: 15px 0; font-size: 26rpx; color: #222;display: flex; flex-direction: column;}
	.indHome .item .tex2{padding-top: 10rpx;}
	.indHome .item image {width:100rpx;height: 100rpx; border-radius: 50%;margin-bottom: 20rpx;margin: 0 auto 20rpx auto; }
	
	.inde_TwoPic{padding: 30rpx 4%;}
	.inde_TwoPic .item{border-radius: 10rpx;overflow: hidden;position: relative; width: 330rpx; height: 200rpx;}
	.inde_TwoPic .item image{ width: 100%; height: 100%; }
	.inde_TwoPic .item .textbox{position: absolute;top: 30rpx;left: 30rpx;color: #fff;}
	.inde_TwoPic .item .tit{font-size: 36rpx; font-weight: bold;letter-spacing: 4rpx;}
	.inde_TwoPic .item .tex{font-size: 24rpx;padding: 10rpx 0;}
	

</style>
