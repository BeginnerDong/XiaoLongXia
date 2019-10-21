<template>
	<view >
		<view class="pdlr4" style="background: #fff0ed;">
			<view class="flexRowBetween pdt40 pdb40">
				<view class="flex font13" style="width:50%;">当前余额<view class="font16" style="margin-left:30rpx">￥0</view></view>
			</view>
		</view>
		<view class="seltTime pdlr4 whiteBj">
			<view class="item flexRowBetween">
				<view class="name font15">交易时间</view>
				<view class="rr flexRowBetween">
					<view class="flex btnbox font12 center color2">
						<view class="btn">全部</view>
						<view class="btn">本月</view>
						<view class="btn">上月</view>
					</view>
					<view @click="zdyiShow">
						<image class="Rarrow" v-show="!is_show" src="../../static/images/mingxi-icon3.png" mode=""></image>
						<image class="Rarrow" v-show="is_show" src="../../static/images/mingxi-icon2.png" mode=""></image>
						
					</view>
				</view>
			</view>
			<view class="item flexRowBetween" v-show="is_show" style="border-top: 2rpx solid  #eee;">
				<view class="name font15">自定义</view>
				<view class="rr flexCenter">
					<view class="btn2 font12">
						开始时间 
						<image class="icon" src="../../static/images/mingxi-icon1.png" mode=""></image>
					</view>
					<view style="padding: 0 20rpx;">至</view>
					<view class="btn2 font12">
						结束时间
						<image class="icon" src="../../static/images/mingxi-icon1.png" mode=""></image>
					</view>
				</view>
			</view>
		</view>
		
		<view class="f5H5"></view>
		<view class="myRowBetween">
			<view class="item flexRowBetween">
				<view class="left">
					<view>充值</view>
					<view class="time">2019-10-21</view>
				</view>
				<view class="right pubColor">+300</view>
			</view>
			<view class="item flexRowBetween">
				<view class="left">
					<view>兑换商品</view>
					<view class="time">2019-10-21</view>
				</view>
				<view class="right">-100</view>
			</view>
		</view>
	</view>	

</template>

<script>
	export default {
		data() {
			return {
				Router:this.$Router,
				is_show:false
			}
		},

		onLoad(options) {
			uni.setStorageSync('canClick', true);
		},

		onShow() {
			const self = this;
			document.title = '余额明细'
		},

		methods: {
			zdyiShow(){
				const self = this;
				self.is_show = !self.is_show
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
	page{padding-bottom: 140rpx;background: #F5F5F5;}
	.dhBtn{width: 140rpx; height: 50rpx; line-height: 50rpx;text-align: center; border-radius: 30rpx;background: #DA251C; color: #fff;}
	.Rarrow{width: 50rpx; height: 50rpx; display: block;}
	.seltTime .item{padding: 30rpx 0;}
	.seltTime .item .name{ width: 140rpx;}
	.seltTime .item .rr{width: 560rpx;}
	.seltTime .item .rr .btnbox .btn{width: 120rpx; height: 50rpx; line-height: 50rpx;border: 2rpx solid #eee;border-radius: 30rpx;margin-left: 30rpx;}
	.seltTime .item .rr .btn2{width: 240rpx; height: 50rpx;line-height: 50rpx;border: 2rpx solid #eee;border-radius: 30rpx; color: #999;padding: 0 60rpx 0 30rpx;box-sizing: border-box;position: relative;}
	.seltTime .item .rr .btn2 .icon{ width: 20rpx; height: 15rpx;position: absolute; top: 50%;right: 10rpx; transform: translateY(-50%);padding: 10rpx;}
</style>
