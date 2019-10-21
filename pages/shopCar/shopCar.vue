<template>
	<view class="" >
		<!--  -->
		<view class="shopOrder pdlr4">
			<view class="item boxShaow radius10 pr flexRowBetween" v-for="(item,index) in proListDate" :key="index">
				<view class="item_selBtn flexCenter">
					<image class="icon" src="../../static/images/address-icon1.png" mode=""></image>
				</view>
				<view class="ll">
					<image class="pic" src="../../static/images/stores-img1.png" mode=""></image>
				</view>
				<view class="rr">
					<view class="titile font15 avoidOverflow2">美味大虾一份</view>
					<view class="flexRowBetween Bmny">
						<view class="flex pubColor font13">
							<view class="price">{{item.price}}</view>
							+
							<view class="priceF">{{item.integral}}</view>
						</view>
						<view class="numBox">
							<view @click="counter(index,'-')">-</view>
							<view class="num">{{item.count}}</view>
							<view @click="counter(index,'+')">+</view>
						</view>
					</view>
				</view>
			</view>
		</view>
		
		<view class="confm_BFix"  style="bottom: 110rpx;">
			<view class="flexRowBetween w">
				<view class="allselt flex">
					<image class="icon" src="../../static/images/address-icon1.png" mode=""></image>
					全选
				</view>
				<view class="flexEnd font13">
					合计： 
					<view class="price">56</view>
					<view class="pubColor">+</view>
					<view class="pubColor">乐豆860</view>
					<view class="btn" @click="Router.navigateTo({route:{path:'/pages/confirmOrder/confirmOrder'}})">结算</view>
				</view>
			</view>
			
		</view>
		
		<!--底部tab键-->
		<view class="navbar">
			<view class="navbar_item" @click="Router.redirectTo({route:{path:'/pages/shop/shop'}})">
				<view class="nav_img">
					<image src="../../static/images/mall-nabar1.png" />
				</view>
				<view class="text">商城首页</view>
			</view>
			<view class="navbar_item" @click="Router.redirectTo({route:{path:'/pages/shopCar/shopCar'}})" >
				<view class="nav_img">
					<image src="../../static/images/mall-nabar2-a.png" />
				</view>
				<view class="text this-text">购物车</view>
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
				proListDate:[
					{price:'28',integral:'860',count:'1'},
					{price:'28',integral:'860',count:'1'}
				],
			}
		},

		onLoad(options) {
			uni.setStorageSync('canClick', true);
		},

		onShow() {
			const self = this;
			document.title = '购物车'
		},

		methods: {
			counter(index,type) {
				const self = this;
				if (type == '+') {
					self.proListDate[index].count++;
				} else {
					if (self.proListDate[index].count > 1) {
						self.proListDate[index].count--;
					}
				};
				self.$Utils.setStorageArray('cartData', self.proListDate[index], 'id', 999);
				self.countTotalPrice();
			},
			getMainData() {
				const self = this;
				self.$apis.userGet(postData, callback);
			}
		}
	}
</script>

<style>
	@import "../../assets/style/shop.css";
	@import "../../assets/style/navbar.css";
	@import "../../assets/style/confm_BFix.css";
	
	page{padding-bottom: 240rpx;background: #F5F5F5;}
	
	.shopOrder .item .ll .pic{ width: 180rpx; height: 180rpx; margin-right: 10rpx;}
	.shopOrder .item .rr{ width: 400rpx; height: 180rpx;}
	.datt{padding-bottom: 20rpx; }
	.shopOrder .item{ padding: 30rpx 20rpx;}
	.bBtn{padding-top: 20rpx;}
	.bBtn .btn{ padding: 0 20rpx; line-height: 50rpx; height: 50rpx; border-radius: 10rpx; color: #666; border:2rpx solid #ccc;font-size: 24rpx; margin-left: 20rpx;}
	
	.item_selBtn{ padding-right: 10rpx; height: 180rpx;}
	.item_selBtn .icon{width: 40rpx; height: 40rpx; display: block;}
	.allselt .icon{ width: 40rpx; height: 40rpx; display: block; margin-right: 10rpx;}
	
</style>
