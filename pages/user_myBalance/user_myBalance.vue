<template>
	<view >
		<view class="pdlr4" style="background: #fff0ed;">
			<view class="flexRowBetween pdt40 pdb40">
				<view class="flex font13" style="width:50%;">当前余额<view class="font16" style="margin-left:30rpx">￥0</view></view>
				<view class="dhBtn font12" @click="Router.navigateTo({route:{path:'/pages/user_myBalance_detail/user_myBalance_detail'}})">余额明细</view>
			</view>
		</view>
		<view class="pdlr4 pdt15 whiteBj">
			<view class="flexRowBetween">
				<view class="">余额充值</view>
				<view class="color3 font12">联系我们：<text style="color: #ff8b7d;">021-56235638</text></view>
			</view>
			<view class="amountLis flexRowBetween pdt15" >
				<view class="item" :class="curr==index?'on':''" v-for="(item,index) in amountLis" :key="index" @click="chageCurr(index)">
					<view class="mny">300元</view>
					<view class="font12 color2">到账：310元</view>
				</view>
			</view>
		</view>
		
		<view class="under_agreeBtn">
			<view class="pdlr4 whiteBj">
				<view class="agreeSel" @click="xieyiAlert">
					<view class="selt" style="margin-right: 16rpx;" @click="seltBtn">
						<image v-show="!is_show" src="../../static/images/address-icon1.png" mode=""></image>
						<image v-show="is_show" src="../../static/images/address-icon.png" mode=""></image>
					</view>
					<view class="text flex">我已阅读并同意<view class="pubColor" @click="Router.navigateTo({route:{path:'/pages/user_myBalance_xieyi/user_myBalance_xieyi'}})">《充值服务章程及协议》</view></view>
				</view>
			</view>
			<view class="submitbtn pdt20 pdb20">
				<button v-show="!is_show" type="submit" style="background: #e0e0e0;">立即充值</button>
				<button v-show="is_show" type="submit">立即充值</button>
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
				amountLis:[{},{},{}],
				curr:0
			}
		},

		onLoad(options) {
			uni.setStorageSync('canClick', true);
		},

		onShow() {
			const self = this;
			document.title = '我的余额'
		},

		methods: {
			chageCurr(index){
				const self = this;
				self.curr = index
			},
			seltBtn(){
				const self = this;
				self.is_show =!self.is_show
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
	.amountLis{align-items: flex-start; flex-wrap: wrap;}
	.amountLis .item{width: 330rpx;border-radius: 10rpx;padding:20rpx;box-sizing: border-box; text-align: center;border: 2rpx solid #E1E1E1; margin-bottom: 30rpx;}
	.amountLis .item .mny{font-size: 30rpx; color: #DA251C;padding-bottom: 10rpx;}
	.amountLis .item.on{background: #ffefed;border-color: #DA251C;}
	
	.agreeSel{padding: 20rpx 0;width: 100%;}
	.under_agreeBtn{width: 100%;position: fixed; bottom: 0;left: 0;}
</style>
