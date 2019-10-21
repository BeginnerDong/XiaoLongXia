<template>
	<view class="" >
		<!--  -->
		<view class="flexRowBetween oneMain pdlr4">
			<view class="font13 flex">积分<text class="font20" style="margin-left: 20rpx;">0</text></view>
			<view class="flexEnd fs12 color3"  @click="Router.navigateTo({route:{path:'/pages/shopOrder/shopOrder'}})">查看商城订单<image class="arrowR" src="../../static/images/about-icon7.png" mode=""></image></view>
		</view>
		
		<view class="pdlr4">
			<view class="orderNav">
				<view class="tt" :class="num==1?'on':''" @click="change('1')">
					<view>全部</view>
				</view>
				<view class="tt" :class="num==2?'on':''" @click="change('2')">
					<view>卡券</view>
				</view>
				<view class="tt" :class="num==3?'on':''" @click="change('3')">
					<view>实物</view>
				</view>
			</view>
		
			<view class="shopOrder">
				<view class="item boxShaow radius10 pr flex" @click="Router.navigateTo({route:{path:'/pages/shopDetail/shopDetail'}})">
					<image class="LT_icon" src="../../static/images/mall-icon.png" mode=""></image>
					<view class="ll">
						<image class="pic" src="../../static/images/mall-img.png" mode=""></image>
					</view>
					<view class="rr">
						<view class="titile font15 avoidOverflow2">美味大虾一份</view>
						<view class="flexRowBetween Bmny">
							<view class="priceF">860</view>
							<view class="buyBtn font12">立即下单</view>
						</view>
					</view>
				</view>
				<view class="item boxShaow radius10 pr flex" @click="Router.navigateTo({route:{path:'/pages/shopDetail/shopDetail'}})">
					<image class="LT_icon" src="../../static/images/mall-icon1.png" mode=""></image>
					<view class="ll">
						<image class="pic" src="../../static/images/mall-img.png" mode=""></image>
					</view>
					<view class="rr">
						<view class="titile font15 avoidOverflow2">美味大虾一份</view>
						<view class="flexRowBetween Bmny">
							<view class="flex pubColor">
								<view class="price">29</view>
								+
								<view class="priceF">860</view>
							</view>
							
							<view class="buyBtn font12">立即下单</view>
						</view>
					</view>
				</view>
			</view>
		</view>
		
		<!--底部tab键-->
		<view class="navbar">
			<view class="navbar_item" @click="Router.redirectTo({route:{path:'/pages/shop/shop'}})">
				<view class="nav_img">
					<image src="../../static/images/mall-nabar1-a.png" />
				</view>
				<view class="text this-text">商城首页</view>
			</view>
			<view class="navbar_item" @click="Router.redirectTo({route:{path:'/pages/shopCar/shopCar'}})" >
				<view class="nav_img">
					<image src="../../static/images/mall-nabar2.png" />
				</view>
				<view class="text">购物车</view>
			</view>
			<view class="navbar_item" @click="Router.redirectTo({route:{path:'/pages/shopOrder/shopOrder'}})">
				<view class="nav_img">
					<image src="../../static/images/mall-nabar3.png" />
				</view>
				<view class="text">订单</view>
			</view>
		</view>
		<!--底部tab键 end-->
	</view>

</template>

<script>
	export default {
		data() {
			return {
				Router:this.$Router,
				num:1
			}
		},

		onLoad(options) {
			uni.setStorageSync('canClick', true);
		},

		onShow() {
			const self = this;
			document.title = '商城'
		},

		methods: {
			change(num){
				const self = this;
				if(num!=self.num){
					self.num = num
				}
			},
			getMainData() {
				const self = this;
				self.$apis.userGet(postData, callback);
			}
		}
	}
</script>

<style>
	@import "../../assets/style/NavTab.css";
	@import "../../assets/style/shop.css";
	@import "../../assets/style/navbar.css";
	page{padding-bottom: 60rpx;background: #F5F5F5;}
	.orderNav{margin-top: 10rpx;}
	.orderNav .tt{width: 33.3%; color: #222;}
	.oneMain{line-height: 100rpx; height: 100rpx;background: #ffefee;}
	
	
</style>
