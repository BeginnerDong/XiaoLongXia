<template>  
    <view>  
		<view class="pdlr4">
			<image style="width: 100%; height: 340rpx;margin-top: 30rpx;" src="../../static/images/choujiang-img.png" mode=""></image>
		</view>
		<view class="pubColor center font15" style="padding: 50rpx 4%;">恭喜你中奖了！</view>
		
		<view class="couponList pdlr4">
			<view class="item flexRowBetween boxShaow radius10 pr oh">
				<image class="fxIcon" src="../../static/images/coupons_fx.png" mode=""></image>
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
		</view>
		<view class="submitbtn" style="margin-top: 200rpx;">
			<button type="button" @click="Router.switchTab({route:{path:'/pages/index/index'}})" class="canvas-btn">立即使用</button>
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
			};  
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

    }  
</script>

<style>  
 @import "../../assets/style/coupon.css";
 
 page{padding-bottom: 60rpx;}
</style>