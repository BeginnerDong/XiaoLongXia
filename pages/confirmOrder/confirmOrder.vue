<template>
	<view class="" >
		
		<view class="">
			<view class="shopOrder pdlr4 pdb15">
				<view class="item boxShaow radius10 pr flex" v-for="(item,index) in proListDate" :key="index">
					<view class="ll">
						<image class="pic" src="../../static/images/stores-img1.png" mode=""></image>
					</view>
					<view class="rr">
						<view class="titile font15 avoidOverflow2">美味大虾一份</view>
						<view class="flexRowBetween Bmny">
							<view class="flex pubColor">
								<view class="price">{{item.price}}</view>
								+
								<view class="priceF">{{item.integral}}</view>
							</view>
							<view class="numBox" style="position: absolute; right: 0; bottom: 0;">
								<view @click="counter(index,'-')">-</view>
								<view class="num">{{item.count}}</view>
								<view @click="counter(index,'+')">+</view>
							</view>
						</view>
					</view>
				</view>
			</view>
		
			<view class="f5H5"></view>
			<view style="padding: 30rpx 4%;">
				<view class="font14" style="color: #fe8e88; padding-bottom: 14rpx;">支付成功后将发送至您的优惠券中</view>
				<view class="font13 color3">请注意查收</view>
			</view>
			<view class="f5H5"></view>
			<view class="pdlr4">
				<view class="pdt40">备注信息</view>
				<view class="bzEdit">
					<textarea value="" placeholder="" />
				</view>
			</view>
			
			<view class="confm_BFix">
				合计： 
				<view class="price">56</view>
				<view class="pubColor">+</view>
				<view class="pubColor">乐豆860</view>
				<view class="btn" @click="Utils.stopMultiClick(submit)">支付</view>
			</view>
			
		</view>
	</view>

</template>

<script>
	export default {
		data() {
			return {
				Router:this.$Router,
				proListDate:[{price:'28',integral:'860',count:'1'}]
			}
		},

		onLoad(options) {
			uni.setStorageSync('canClick', true);
		},

		onShow() {
			const self = this;
			document.title = '确认订单'
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
	@import "../../assets/style/confm_BFix.css";
	page{padding-bottom: 60rpx;}
	.storesOrder{margin-bottom: 30rpx;}
	.bzEdit textarea{ width: 100%; height: 230rpx;box-sizing: border-box;padding: 20rpx;background: #f3f3f3; font-size: 26rpx;border-radius: 10rpx; display: block;margin-top: 20rpx;}
	

</style>
