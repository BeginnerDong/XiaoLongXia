<template>
	<view class="" >
		<!--  -->
		<view class="pdlr4 whiteBj">
			<view class="orderNav">
				<view class="tt" :class="num==1?'on':''" @click="change('1')">
					<view>全部</view>
				</view>
				<view class="tt" :class="num==2?'on':''" @click="change('2')">
					<view>待完成</view>
				</view>
				<view class="tt" :class="num==3?'on':''" @click="change('3')">
					<view>已完成</view>
				</view>
			</view>
		</view>
		
		<view class="shopOrder pdlr4">
			<view class="item boxShaow radius10">
				<view class="datt flexRowBetween font12">
					<view class="left">
						<view class="color3" style="margin-bottom: 10rpx;">交易时间：2019-10-21</view>
					</view>
					<view class="state pubColor">等待完成</view>
				</view>
				<view class="flex">
					<view class="ll">
						<image class="pic" src="../../static/images/mall-img.png" mode=""></image>
					</view>
					<view class="rr">
						<view class="titile font15 avoidOverflow2">团队聚餐</view>
						<view class="text pdt10 color2 font13">2018-08-09 14:00-16:00</view>
					</view>
				</view>
				<view class="bBtn flexRowBetween font12">
					<view class="pubColor">预约号：235232</view>
					<view class="btn">确认完成</view>
				</view>
			</view>
			<view class="item boxShaow radius10">
				<view class="datt flexRowBetween font12">
					<view class="left">
						<view class="color3" style="margin-bottom: 10rpx;">交易时间：2019-10-21</view>
					</view>
					<view class="state pubColor">已经完成</view>
				</view>
				<view class="flex">
					<view class="ll">
						<image class="pic" src="../../static/images/mall-img.png" mode=""></image>
					</view>
					<view class="rr">
						<view class="titile font15 avoidOverflow2">团队聚餐</view>
						<view class="text pdt10 color2 font13">2018-08-09 14:00-16:00</view>
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
				Router:this.$Router,
				num:1
			}
		},

		onLoad(options) {
			uni.setStorageSync('canClick', true);
		},

		onShow() {
			const self = this;
			document.title = '我的预订'
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
	page{padding-bottom: 60rpx;background: #F5F5F5;}
	.orderNav{margin-top: 10rpx;}
	.orderNav .tt{width: 33.3%; color: #222;}
	
	.shopOrder .item .ll .pic{ width: 180rpx; height: 180rpx;}
	.shopOrder .item .rr{ height: 180rpx;}
	.datt{padding-bottom: 20rpx; }
	.shopOrder .item{ padding: 30rpx;}
	.bBtn{padding-top: 20rpx;}
	.bBtn .btn{ padding: 0 20rpx; line-height: 50rpx; height: 50rpx; border-radius: 10rpx; color: #666; border:2rpx solid #ccc;font-size: 24rpx; margin-left: 20rpx;}
	
</style>
