<template>
	<view class="" >
		<!--  -->
		<view class="w">
			<image style="width: 100%; height: 340rpx;" src="../../static/images/party-img1.png" mode=""></image>
		</view>
		
		<view class="pdlr4">
			<view class="orderNav">
				<view class="tt" :class="num==1?'on':''" @click="change('1')">
					<image class="icon" src="../../static/images/party-icon2.png" mode=""></image>
					<view>包间</view>
				</view>
				<view class="tt" :class="num==2?'on':''" @click="change('2')">
					<image class="icon" src="../../static/images/party-icon1.png" mode=""></image>
					<view>大堂</view>
				</view>
			</view>
		</view>
		<view class="f5H5"></view>
		
		<view class="" v-show="num==1">
			<view class="infor-title center">
				<view class="tt">龙虾DIY</view>
			</view>
			<view class="xqInfor">
				<view class="cont">
					<view class="color1">详情介绍</view>
					<view>公司团建用餐、亲朋好友聚会不二选。</view>
					<view>餐厅提供定制分为装饰，神秘环节等个性定制增值服务。</view>
					<view>提前预定，餐厅将为您预留位置，到店用餐不排队，上餐时间自由控制。</view>
					<view>食堂点餐需要提前确定，请电话联系餐厅经理，1对1为您服务，活动现场除生日蛋糕，请勿外带其他视频。</view>
					<view>
						<image class="w" style="width: 100%; height: 400rpx;" src="../../static/images/party-img2.png" mode="widthFix"></image>
					</view>
					<view><text class="color1 fs14">预定须知</text></view>
					<view>1、该活动适合总人数8人以上生日会</view>
					<view>2、至少提前2天进行线上预定</view>
					<view>3、预定成功后，请提前联系餐厅经理确认点餐等事宜</view>
					<view>4、活动当天请向工作人员出示预定信息，即可参加</view>
					<view><text class="color1 fs14">预定须知</text></view>
					<view>1、如需取消，请提前48小时在线提交退订申请</view>
					<view>2、如需改期，请提前48小时取消订单，后重新新订单预定申请</view>
					<view>3、活动前48小时内，不能取消或改期订单</view>
					<view>4、活动当天向餐厅工作人员出示预定信息可参加</view>
				</view>
			</view>
		</view>
		<view class="" v-show="num==2">
			<view class="infor-title center">
				<view class="tt">大堂DIY</view>
			</view>
			<view class="xqInfor">
				<view class="cont">
					<view class="color1">大堂详情介绍</view>
					<view>公司团建用餐、亲朋好友聚会不二选。</view>
					<view>餐厅提供定制分为装饰，神秘环节等个性定制增值服务。</view>
					<view>提前预定，餐厅将为您预留位置，到店用餐不排队，上餐时间自由控制。</view>
					<view>食堂点餐需要提前确定，请电话联系餐厅经理，1对1为您服务，活动现场除生日蛋糕，请勿外带其他视频。</view>
					<view>
						<image class="w" style="width: 100%; height: 400rpx;" src="../../static/images/details-img.png" mode="widthFix"></image>
					</view>
					<view><text class="color1 fs14">预定须知</text></view>
					<view>1、该活动适合总人数8人以上生日会</view>
					<view>2、至少提前2天进行线上预定</view>
					<view>3、预定成功后，请提前联系餐厅经理确认点餐等事宜</view>
					<view>4、活动当天请向工作人员出示预定信息，即可参加</view>
					<view><text class="color1 fs14">预定须知</text></view>
					<view>1、如需取消，请提前48小时在线提交退订申请</view>
					<view>2、如需改期，请提前48小时取消订单，后重新新订单预定申请</view>
					<view>3、活动前48小时内，不能取消或改期订单</view>
					<view>4、活动当天向餐厅工作人员出示预定信息可参加</view>
				</view>
			</view>
		</view>
		
		<view class="xqbotomBar">
			<view class="submitbtn w"><button type="button" @click="Router.navigateTo({route:{path:'/pages/HappyParty_booking/HappyParty_booking'}})">我要预定</button></view>
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
			document.title = '开心派对'
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
	@import "../../assets/style/prodctDetail.css";
	page{padding-bottom: 180rpx;}
	.orderNav{height: auto;}
	.orderNav .tt{padding: 40rpx 0 30rpx 0; line-height: 40rpx;}
	.orderNav .on{color: #222;}
	.orderNav .tt .icon{width: 67rpx; height: 67rpx; display: block; margin: 0 auto 20rpx auto;}
	.orderNav .on::after{width: 120rpx;}
	.xqbotomBar{height: 140rpx;}

</style>
