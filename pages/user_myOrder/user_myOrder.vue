<template>
	<view class="" >
		
		<view class="tooling_indNav f5bj pdlr4">
			<view class="list">
				<view class="item" :class="curr==1?'on':''" @click="changeOne('1')">门店订单</view>
				<view class="item" :class="curr==2?'on':''" @click="changeOne('2')">积分商城订单</view>
			</view>
		</view>
		<!--  -->
		<view v-show="curr==1">
			<view class="orderNav whiteBj">
				<view class="tt" :class="num==1?'on':''" @click="change('1')">
					<view>全部</view>
				</view>
				<view class="tt" :class="num==2?'on':''" @click="change('2')">
					<view>待取货</view>
				</view>
				<view class="tt" :class="num==3?'on':''" @click="change('3')">
					<view>已取货</view>
				</view>
			</view>
		
			<view class="shopOrder pdlr4">
				<view class="item boxShaow radius10">
					<view class="datt flexRowBetween font12">
						<view class="left">
							<view class="color3" style="margin-bottom: 10rpx;">交易时间：2019-10-21</view>
						</view>
						<view class="state pubColor">等待取货</view>
					</view>
					<view class="flex">
						<view class="ll">
							<image class="pic" src="../../static/images/mall-img.png" mode=""></image>
						</view>
						<view class="rr">
							<view class="titile font15 avoidOverflow2">美味大虾一份</view>
							<view class="Bmny flex pubColor">
								<view class="price">29</view>
								<view>+</view>
								<view class="priceF">860</view>
							</view>
						</view>
					</view>
				</view>
				<view class="item boxShaow radius10">
					<view class="datt flexRowBetween font12">
						<view class="left">
							<view class="color3" style="margin-bottom: 10rpx;">交易时间：2019-10-21</view>
						</view>
						<view class="state pubColor">已经取货</view>
					</view>
					<view class="flex">
						<view class="ll">
							<image class="pic" src="../../static/images/mall-img.png" mode=""></image>
						</view>
						<view class="rr">
							<view class="titile font15 avoidOverflow2">美味大虾一份</view>
							<view class="Bmny flex pubColor">
								<view class="price">29</view>
								<view>+</view>
								<view class="priceF">860</view>
							</view>
						</view>
					</view>
				</view>
			</view>
		</view>
		<view v-show="curr==2">
			<view class="orderNav whiteBj">
				<view class="tt" :class="num==1?'on':''" @click="change('1')">
					<view>全部</view>
				</view>
				<view class="tt" :class="num==2?'on':''" @click="change('2')">
					<view>待发货</view>
				</view>
				<view class="tt" :class="num==3?'on':''" @click="change('3')">
					<view>已发货</view>
				</view>
				<view class="tt" :class="num==4?'on':''" @click="change('4')">
					<view>已完成</view>
				</view>
			</view>
			<view class="shopOrder pdlr4">
				<view class="item boxShaow radius10">
					<view class="datt flexRowBetween font12">
						<view class="left">
							<view class="color3" style="margin-bottom: 10rpx;">交易时间：2019-10-21</view>
						</view>
						<view class="state pubColor">等待发货</view>
					</view>
					<view class="flex">
						<view class="ll">
							<image class="pic" src="../../static/images/mall-img.png" mode=""></image>
						</view>
						<view class="rr">
							<view class="titile font15 avoidOverflow2">美味大虾一份</view>
							<view class="Bmny flex pubColor">
								<view class="price">29</view>
								<view>+</view>
								<view class="priceF">860</view>
							</view>
						</view>
					</view>
				</view>
				<view class="item boxShaow radius10">
					<view class="datt flexRowBetween font12">
						<view class="left">
							<view class="color3" style="margin-bottom: 10rpx;">交易时间：2019-10-21</view>
						</view>
						<view class="state pubColor">已经发货</view>
					</view>
					<view class="flex">
						<view class="ll">
							<image class="pic" src="../../static/images/mall-img.png" mode=""></image>
						</view>
						<view class="rr">
							<view class="titile font15 avoidOverflow2">美味大虾一份</view>
							<view class="Bmny flex pubColor">
								<view class="price">29</view>
								<view>+</view>
								<view class="priceF">860</view>
							</view>
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
				num:1,
				curr:1
			}
		},

		onLoad(options) {
			uni.setStorageSync('canClick', true);
		},

		onShow() {
			const self = this;
			document.title = '我的订单'
		},

		methods: {
			changeOne(curr){
				const self = this;
				if(curr!=self.curr){
					self.curr = curr
				}
			},
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
	.tooling_indNav{padding: 20rpx 4%;}
	.tooling_indNav .list .item{width: 50%;}
	.orderNav .tt{width: 33.3%; color: #222;}
	
	.shopOrder .item .ll .pic{ width: 180rpx; height: 180rpx;}
	.shopOrder .item .rr{ height: 180rpx;}
	.datt{padding-bottom: 20rpx; }
	.shopOrder .item{ padding: 30rpx;}
	.priceF::before{content: "乐豆";font-weight: normal;}
	
</style>
