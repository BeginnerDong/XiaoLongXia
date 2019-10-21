<template>
	<view>
		<view class="pdlr4 store_order">
			<view class="ftw pubname pdt20 pdb10">已选商品</view>
			<view class="pdb10 font12 color2">正价区</view>
			<view class="selt_list">
				<view class="item font12 flexRowBetween ">
					<view class="flex">
						<view class="selt_tit">乐中辣鸡翅</view>
						<view>×1</view>
					</view>
					<view class="">￥36</view>
				</view>
				<view class="item font12 flexRowBetween">
					<view class="flex">
						<view class="selt_tit">乐中辣鸡翅</view>
						<view>×1</view>
					</view>
					<view class="">￥36</view>
				</view>
			</view>
			<view class="borderB1"></view>
			<view class="pdt15 pdb10 font12 color2">超值架构(限一份)</view>
			<view class="selt_list">
				<view class="item font12 flexRowBetween ">
					<view class="flex">
						<view class="selt_tit">乐中辣鸡翅</view>
						<view>×1</view>
					</view>
					<view class="">￥36</view>
				</view>
			</view>
			<view class="specsIndex flex borderB1">
				<view class="item center"  v-for="(item,index) in specsListDate" :key="index">
					<view><image class="pic" src="../../static/images/stores_order-img.png" mode=""></image></view>
					<view class="tit font12">{{item.title}}</view>
					<view class="font12">(加购价)</view>
					<view class="price">9.9</view>
				</view>
			</view>
			<view class="">
				<view class="ftw pdt10 pdb5 flexRowBetween">
					<view>选择优惠</view>
					<view class="flexEnd">
						<image class="arrowR" src="../../static/images/about-icon7.png" mode=""></image>
					</view>
				</view>
				<view class="color2 pdb10">无可用优惠券</view>
			</view>
		</view>
		<view class="f5H5"></view>
		<view class="pdlr4">
			<view class="pdtb10 borderB1 pubColor">充值后支付更优惠哦，请选择充值金额:</view>
			<view class="pdtb10 borderB1 seltCoupon" v-for="(item,index) in seltCoupon" :key="index">
				<view class="flex one">	
					<view class="L-icon"><image :src="item.iconUrl" mode=""></image></view>
					<view class="tex font13 avoidOverflow">{{item.cpName}}</view>
					<view class="xqBtn"><view class="btn" v-show="item.is_xqBtn" @click="xqBtnOpen">详情</view></view>
					<view class="seltBtn flexEnd">
						<image class="icon" src="../../static/images/address-icon1.png" mode=""></image>
					</view>
				</view>
				<view class="couponList" v-show="is_coupon">
					<view class="item flexRowBetween boxShaow radius10 oh">
						<view class="L">
							<image src="../../static/images/choujiang-icon.png" mode=""></image>
						</view>
						<view class="R">
							<view>15元现金券</view>
							<view class="mny font12 color3">满16元<text class="price font16 ftw">9.00</text></view>
							<view class="flexEnd">
								<view class="btn">查看详情</view>
							</view>
						</view>
					</view>
					<view class="item flexRowBetween boxShaow radius10 oh">
						<view class="L">
							<image src="../../static/images/stores_order-img.png" mode=""></image>
						</view>
						<view class="R">
							<view>15元现金券</view>
							<view class="mny font12 color3">满16元<text class="price font16 ftw">9.00</text></view>
							<view class="flexEnd">
								<view class="btn">查看详情</view>
							</view>
						</view>
					</view>
				</view>
			</view>
		</view>
		
		<!-- 底部菜单按钮 -->
		<view class="xqbotomBar">
			<view class="twoNav center w flex">
				<view class="item L flexCenter">
					<view class="white font12 flex">总计：<view class="price font13">36</view></view>
				</view>
				<view class="item R flexCenter" >
					<view class="white">微信支付</view>
				</view>
			</view>
		</view>
		
		
	</view>
</template>
<script>
	export default {
		data() {
			return {
				Router:this.$Router,
				is_show:false,
				specsListDate:[{},{},{}],
				is_coupon:false,
				seltCoupon:[
					{iconUrl:'../../static/images/stores_order-icon3.png',is_xqBtn:true,cpName:'充值300元,送价值68元券'},
					{iconUrl:'../../static/images/stores_order-icon3.png',is_xqBtn:true,cpName:'充值500元，送价值108元券'},
					{iconUrl:'../../static/images/stores_order-icon3.png',is_xqBtn:true,cpName:'充值800元，送价值156元券'},
					{cpName:'暂不充值',is_xqBtn:false}
				]
			}
		},

		onLoad(options) {
			// uni.setStorageSync('canClick', true);
		},

		onShow() {
			const self = this;
			document.title = '提交订单'
		},

		methods: {
			xqBtnOpen(){
				const self = this;
				self.is_coupon=!self.is_coupon
			},
			getMainData() {
				const self = this;
				console.log('852369')
				const postData = {};
				postData.tokenFuncName = 'getProjectToken';
				self.$apis.orderGet(postData, callback);
			},
		}
	}
</script>

<style>
	@import "../../assets/style/coupon.css";
	@import "../../assets/style/prodctDetail.css";
	page{padding-bottom:140rpx;}
	
	.xqbotomBar{z-index: 90;}
	
	/* .store_order .pubname{padding: 40rpx 0 30rpx 0;} */
	.selt_list{padding-bottom: 10rpx;}
	.selt_list .item{padding-bottom: 10rpx;}
	.selt_tit{margin-right: 20rpx;}
	
	.specsIndex{flex-wrap: wrap;align-items: flex-start;}
	.specsIndex .item{width: 210rpx;  height: 250rpx; border: 2rpx solid #eee;border-radius: 10rpx;overflow: hidden;margin-right: 30rpx;box-sizing: border-box;margin:0 30rpx 30rpx 0;}
	.specsIndex .item:nth-of-type(3n){margin-right: 0;}
	.specsIndex .item .pic{ width: 152rpx; height: 112rpx; display: block; margin: 20rpx auto;}
	.specsIndex .numBox .redBj{background: #DA251C; color: #fff;}
	
	.seltCoupon .one .L-icon{width: 24rpx; height: 30rpx; display: block; margin-right: 10rpx;}
	.seltCoupon .one .L-icon image{width: 100%; height: 100%; display: block;}
	.seltCoupon .one .tex{width: 400rpx;font-size: 26rpx;}
	.seltCoupon .one .xqBtn{width: 100rpx;margin: 0 20rpx ;}
	.seltCoupon .one .xqBtn .btn{width: 100%; height: 40rpx; line-height: 40rpx;text-align: center;color: #666;font-size: 24rpx;border-radius: 30rpx;border: 2rpx solid #eee;}
	.seltCoupon .one .seltBtn{width: 100rpx; }
	.seltCoupon .one .seltBtn .icon{width: 40rpx; height: 40rpx; display: block;}
</style>
