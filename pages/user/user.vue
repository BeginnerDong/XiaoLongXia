<template>
	<view>
		

		<view class="userHead pr">
			<view class="left">
				<image class="photo" src="../../static/images/about-img.png" mode=""></image>
				快乐的猫
			</view>
			<view class="boxShaow radius10 integralData flexRowBetween">
				<view class="item center">
					<view class="number color1">300</view>
					<view class="font12 color2">积分</view>
				</view>
				<view class="item center">
					<view class="number color1">100</view>
					<view class="font12 color2">余额</view>
				</view>
			</view>
		</view>
		
		<view class="XlineNav pdlr4 whiteBj" style="padding-top: 70rpx;">
			<view class="item flexRowBetween"  @click="Router.navigateTo({route:{path:'/pages/user_myBalance/user_myBalance'}})">
				<view class="ll flex">
					<image class="icon" src="../../static/images/about-icon.png"></image>
					<view class="ilblock">我要充值</view>
				</view>
				<view class="rr">
					<image class="arrowR" src="../../static/images/about-icon7.png" ></image>
				</view>
			</view>
			<view class="item flexRowBetween" @click="Router.navigateTo({route:{path:'/pages/user_information/user_information'}})">
				<view class="ll flex">
					<image class="icon" src="../../static/images/about-icon1.png"></image>
					<view class="ilblock">个人信息</view>
				</view>
				<view class="rr">
					<image class="arrowR" src="../../static/images/about-icon7.png" ></image>
				</view>
			</view>
			<view class="item flexRowBetween" @click="Router.navigateTo({route:{path:'/pages/user_myOrder/user_myOrder'}})">
				<view class="ll flex">
					<image class="icon" src="../../static/images/about-icon2.png"></image>
					<view class="ilblock">我的订单</view>
				</view>
				<view class="rr">
					<image class="arrowR" src="../../static/images/about-icon7.png" ></image>
				</view>
			</view>
			<view class="item flexRowBetween" @click="Router.navigateTo({route:{path:'/pages/user_myBooking/user_myBooking'}})">
				<view class="ll flex">
					<image class="icon" src="../../static/images/about-icon3.png"></image>
					<view class="ilblock">我的预订</view>
				</view>
				<view class="rr">
					<image class="arrowR" src="../../static/images/about-icon7.png" ></image>
				</view>
			</view>
			<view class="item flexRowBetween" @click="Router.switchTab({route:{path:'/pages/coupon/coupon'}})">
				<view class="ll flex">
					<image class="icon" src="../../static/images/about-icon4.png"></image>
					<view class="ilblock">我的优惠券</view>
				</view>
				<view class="rr">
					<image class="arrowR" src="../../static/images/about-icon7.png" ></image>
				</view>
			</view>
			<view class="item flexRowBetween" @click="Router.navigateTo({route:{path:'/pages/setCard/setCard'}})">
				<view class="ll flex">
					<image class="icon" src="../../static/images/about-icon5.png"></image>
					<view class="ilblock">我的集点卡</view>
				</view>
				<view class="rr">
					<image class="arrowR" src="../../static/images/about-icon7.png" ></image>
				</view>
			</view>
			<view class="item flexRowBetween" @click="Router.navigateTo({route:{path:'/pages/user_integral/user_integral'}})">
				<view class="ll flex">
					<image class="icon" src="../../static/images/about-icon6.png"></image>
					<view class="ilblock">我的积分</view>
				</view>
				<view class="rr">
					<image class="arrowR" src="../../static/images/about-icon7.png" ></image>
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
				showView: false,
				score:'',
				wx_info:{}
			}
		},
		onLoad() {
			const self = this;
			//self.$Utils.loadAll(['getMainData'], self);
		},
		methods: {

			getMainData() {
				const self = this;
				console.log('852369')
				const postData = {};
				postData.tokenFuncName = 'getProjectToken';

				const callback = (res) => {
					if (res.solely_code == 100000 && res.info.data[0]) {
						self.mainData = res.info.data;
					} else {
						self.$Utils.showToast(res.msg, 'none')
					};
					self.$Utils.finishFunc('getMainData');

				};
				self.$apis.orderGet(postData, callback);

			},

		},
	};
</script>

<style>
	page{background: #F5F5F5;}
	.userHead{height: 320rpx;background: #da251c;padding:50rpx 4% 0rpx 4%;color: #fff;font-size: 28rpx;box-sizing: border-box;}
	.userHead .photo{width: 120rpx;height: 120rpx;border-radius: 50%;margin-right: 20rpx;}
	.userHead .left{display: flex;flex-direction: row;align-items: center;}
	
	
	.integralData{background: #fff; padding: 30rpx 0;position: absolute;top: 220rpx; width:92% ;left: 50%;transform: translateX(-50%);}
	.integralData .item{width: 50%;padding: 0 10rpx;box-sizing: border-box;}
	.integralData .item:first-child{border-right: 1px solid #eee;}
	.integralData .item .number{margin-bottom: 10rpx; font-size: 38rpx;}
	

	/* 我的-菜单列表 */
	.XlineNav .item{border-bottom: solid 1rpx #eee;box-sizing: border-box;height: 100rpx;font-size: 28rpx;}
	.XlineNav .item:last-child{border-bottom: 0;}
	.XlineNav .item .ll .icon{width: 30rpx;height: 30rpx;margin-right: 20rpx; display: block;}
	.XlineNav .item .ll .icon image{height:100%;width: 100%;}
	.XlineNav .info .arrow{width: 12rpx;height: 24rpx;position: absolute;right: 4%;top: 50%;transform: translateY(-50%);}
		
		

</style>
