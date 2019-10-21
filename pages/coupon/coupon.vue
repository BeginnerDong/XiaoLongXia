<template>
	<view class="" >
		<!--  -->
			<view class="tooling_indNav" style="padding: 0;">
				<view class="list">
					<view class="item" :class="num==1?'on':''" @click="change('1')">未使用</view>
					<view class="item" :class="num==2?'on':''" @click="change('2')">已使用</view>
					<view class="item" :class="num==3?'on':''" @click="change('3')">已过期</view>
					<view class="item" :class="num==4?'on':''" @click="change('4')">已分享</view>
				</view>
			</view>
			<view class="pdlr4">
				<view class="couponList" v-show="num==1">
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
				<view class="couponList" v-show="num==2">
					<view class="item flexRowBetween boxShaow radius10 pr oh">
						<image class="userIcon" src="../../static/images/coupons-icon.png" mode=""></image>
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
				<view class="couponList" v-show="num==3">
					<view class="item flexRowBetween boxShaow radius10 pr oh">
						<image class="userIcon" src="../../static/images/coupons-icon1.png" mode=""></image>
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
				<view class="couponList" v-show="num==4">
					<view class="item flexRowBetween boxShaow radius10 pr oh">
						<image class="userIcon" src="../../static/images/coupons-icon2.png" mode=""></image>
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
			document.title = '优惠券'
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
	@import "../../assets/style/coupon.css";
	page{padding-bottom: 140rpx;background: #F5F5F5;}
	.tooling_indNav .list{border-radius: 0;}
	.tooling_indNav .list .item{line-height: 100rpx;border-right:0 ;}
	
	

</style>
