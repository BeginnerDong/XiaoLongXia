<template>
	<view >
		<view class="pdlr4" style="background: #fff0ed;">
			<view class="flexRowBetween pdt40 pdb40">
				<view class="flex font13" style="width:50%;">积分 <view class="font16" style="margin-left:30rpx">0</view></view>
				<view class="dhBtn font12">积分兑换</view>
			</view>
		</view>
		
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
			document.title = '我的积分'
		},

		methods: {
			getMainData() {
				const self = this;
				self.$apis.userGet(postData, callback);
			}
		}
	}
</script>

<style>
	@import "../../assets/style/NavTab.css";
	page{padding-bottom: 140rpx;}
	.dhBtn{width: 140rpx; height: 50rpx; line-height: 50rpx;text-align: center; border-radius: 30rpx;background: #DA251C; color: #fff;}
</style>
