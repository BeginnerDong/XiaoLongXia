<template>
	<view>
		<!--  -->
		<view class="pdlr4">
			<view class="flexRowBetween pdt40 pdb40">
				<view style="width:520rpx; color: #ff8882; line-height: 40rpx;">每单实际支付每满100元获得1点，兑换后任意消费才可以使用</view>
				<view class="jijdBtn font12" @click="Router.navigateTo({route:{path:'/pages/setCard_detail/setCard_detail'}})">集点明细</view>
			</view>
			<view class="f5bj setCardEight">
				<view class="item" v-for="(item,index) in num" :key="index">{{item}}</view>
			</view>
			<view class="tit_xian pr"><view class="center tt font15">集点奖品</view></view>
			
			<view class="setCardList">
				<view class="item flexRowBetween boxShaow radius10" v-for="(item,index) in setCardList" :key="index">
					<view class="pic"><image src="../../static/images/the_order-img.png" mode=""></image></view>
					<view class="M">
						<view class="title font15 avoidOverflow">美味大虾一份</view>
						<view class="font12 color3 avoidOverflow">肉质肥厚,味道鲜美,富含蛋白质</view>
						<view class="time">有效7天，权限食堂/自提/外卖</view>
					</view>
					<view class="R">
						<view class="btn color2">2点</view>
						<view class="btn pubBj font12">兑换</view>
					</view>
				</view>
			</view>
		</view>
		<view class="submitbtn" style="margin: 88rpx auto;" @click="Router.switchTab({route:{path:'/pages/index/index'}})"><button type="button">立即使用</button></view>
		
		<view class="tit_xian pr" style="margin: 30rpx auto;"><view class="center tt font15">活动规则</view></view>
		<view class="xqInfor">
			<view class="cont">
				<view>1、内容内容内容内容内容内容内容内容</view>
				<view>2、内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容</view>
				<view>3、内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容</view>
			</view>
		</view>
		
	</view>

</template>

<script>
	export default {
		data() {
			return {
				Router:this.$Router,
				num:8,
				setCardList:[{},{},{}]
			}
		},

		onLoad(options) {
			uni.setStorageSync('canClick', true);
		},

		onShow() {
			const self = this;
			document.title = '集点卡'
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
	 page{padding-bottom: 60rpx;}
	.jijdBtn{width: 140rpx; height: 50rpx; line-height: 50rpx;text-align: center; border-radius: 30rpx;background: #DA251C; color: #fff;}
	
	.setCardEight{padding: 50rpx 50rpx 10rpx 50rpx;display: flex;justify-content: flex-start;align-items: center; flex-wrap: wrap;margin-bottom:60rpx;}
	.setCardEight .item{width: 85rpx; height: 99rpx; box-sizing: border-box; line-height: 99rpx;text-align: center; background:url(../../static/images/card-icon1.png) no-repeat 0 0/100% 100%; margin-right: 80rpx; margin-bottom: 40rpx;}
	.setCardEight .item:nth-of-type(4n){margin-right: 0;}

	
	.setCardList .item{padding: 20rpx; align-items: flex-start;margin-bottom: 40rpx;}
	.setCardList .item .pic{width: 200rpx; height: 200rpx; border-radius: 10rpx;overflow: hidden; display: block;}
	.setCardList .item .pic image{width: 100%; height: 100%; display: block;}
	.setCardList .item .M{width: 310rpx; display: block; flex-direction: column;}
	.setCardList .item .M .title{margin-bottom: 10rpx;margin-top: 20rpx;}
	.setCardList .item .M .time{font-size: 20rpx; color: #ff8882;margin-top: 30rpx;}
	.setCardList .item .R{width: 100rpx;margin-top: 40rpx;}
	.setCardList .item .R .btn{width: 100%; height: 60rpx;box-sizing: border-box; text-align: center; line-height: 58rpx;border: 2rpx solid #E7E7E7;}
	.setCardList .item .R .btn.pubBj{border-color: #DA251C; color: #fff;}
</style>
