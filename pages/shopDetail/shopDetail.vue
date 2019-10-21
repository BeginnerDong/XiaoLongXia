<template>
	<view>
		
		<view class="detailxqBan">
			<image src="../../static/images/stores-banner.png" mode=""></image>
		</view>
		
		<view class="detail_one">
			<view class="tit font14">美味大虾标题美味大虾标题美味大虾标题美味大虾标题美味大虾标题</view>
			<view class="flex pubColor">
				<view class="price font14">285</view>
				+
				<view class="priceF font14">860</view>
				<view class="yuanJia">99</view>
			</view>
		</view>
		
		<view class="f5H5"></view>
		<view class="infor-title">
			<view class="tt">商品介绍</view>
		</view>
		<view class="xqInfor">
			<view class="cont">
				<view>兑换此券后，可5折购买奥尔良中翅一对，仅限小程序下凡使用，有效期自领券7天之内</view>
			</view>
		</view>
		<view class="infor-title" style="padding-top: 10rpx;">
			<view class="tt">商品详情</view>
		</view>
		<view class="xqInfor">
			<view class="cont">
				<view>兑换此券后，可5折购买奥尔良中翅一对详情介绍详情介绍详情介绍详情详情介绍详情介绍详情介绍详情详情介绍详情介绍详情介绍详情折购买奥尔良中翅一对详情介绍详情介绍详情介绍详情详情介绍</view>
				<view>
					<image class="w" src="../../static/images/stores-img.png" mode="widthFix"></image>
				</view>
			</view>
		</view>
		<view class="infor-title" style="padding-top: 10rpx;">
			<view class="tt">价格说明</view>
		</view>
		<view class="xqInfor">
			<view class="cont">
				<view>兑换此券后，可5折购买奥尔良中翅一对详情介绍详情介绍详情介绍详情详情介绍详情介绍详情介绍详情详情介绍详情介绍详情介绍详情折购买奥尔良中翅一对详情介绍详情介绍详情介绍详情详情介绍</view>
			</view>
		</view>
		
		<!-- 底部菜单按钮 -->
		<view class="xqbotomBar">
			<view class="threeNav center w flex">
				<view class="item L flexCenter">
					<view class="flexColumn">
						<view><image class="icon" src="../../static/images/details-icon.png" mode=""></image></view>
						<view class="color2 font12">客服</view>
					</view>
					
				</view>
				<view class="item M flexCenter">
					<view class="white">加入购物车</view>
				</view>
				<view class="item R flexCenter" @click="Router.navigateTo({route:{path:'/pages/confirmOrder/confirmOrder'}})">
					<view class="white">立即下单</view>
				</view>
			</view>
		</view>
		
	</view>
	
</template>


<script>
	export default {
		data() {
			return {
				Router:this.$Router
			}
		},

		onLoad(options) {
			uni.setStorageSync('canClick', true);
		},

		onShow() {
			const self = this;
			document.title = '商品详情'
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
	@import "../../assets/style/prodctDetail.css";
	@import "../../assets/style/quill.css";
	
	page{padding-bottom:140rpx;}
	.yuanJia::before{content: "原价￥";}
	

</style>
