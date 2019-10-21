<template>
	<view>
		<view class="pdlr4 store_order">
			<view class="ftw pubname pdt20 pdb10">已选商品</view>
			<view class="pdb10 font12 color2">正价区</view>
			<view class="selt_list">
				<view class="item font12 flexRowBetween ">
					<view class="flex">
						<view class="selt_tit">乐中辣鸡翅</view>
						<view>×1</view>
					</view>
					<view class="">￥36</view>
				</view>
				<view class="item font12 flexRowBetween">
					<view class="flex">
						<view class="selt_tit">乐中辣鸡翅</view>
						<view>×1</view>
					</view>
					<view class="">￥36</view>
				</view>
			</view>
			<view class="borderB1"></view>
			<view class="pdt15 pdb10 font12 color2">超值架构(限一份)</view>
			<view class="selt_list">
				<view class="item font12 flexRowBetween ">
					<view class="flex">
						<view class="selt_tit">乐中辣鸡翅</view>
						<view>×1</view>
					</view>
					<view class="">￥36</view>
				</view>
			</view>
			<view class="specsIndex flex borderB1">
				<view class="item center pr" :class="currSpecs==index?'on':''"  v-for="(item,index) in specsListDate" @click="changeSpecs(index)" :key="index">
					<view class="fxNum">1</view>
					<view><image class="pic" src="../../static/images/stores_order-img.png" mode=""></image></view>
					<view class="tit font12">{{item.title}}</view>
					<view class="font12">(加购价)</view>
					<view class="price">9.9</view>
					<view class="fxDelt">-</view>
				</view>
			</view>
			<view class="" @click="couponShow_alert">
				<view class="ftw pdt10 pdb5 flexRowBetween">
					<view>选择优惠</view>
					<view class="flexEnd">
						<image class="arrowR" src="../../static/images/about-icon7.png" mode=""></image>
					</view>
				</view>
				<view class="color2 pdb10">无可用优惠券</view>
			</view>
		</view>
		<view class="f5H5"></view>
		<view class="pdlr4">
			<view class="pdtb10 borderB1 pubColor">充值后支付更优惠哦，请选择充值金额:</view>
			<view class="seltCoupon">
				<view class="pdtb10 borderB1 seltList">
					<view class="flex one">	
						<view class="L-icon"><image src="../../static/images/stores_order-icon3.png" mode=""></image></view>
						<view class="tex font13 avoidOverflow">充值300元，送价值68元券</view>
						<view class="xqBtn" :class="curr==1?'on':''" @click="openXqBtn('1')"><view class="btn">详情</view></view>
						<view class="seltBtn flexEnd">
							<image class="icon" src="../../static/images/address-icon1.png" mode=""></image>
						</view>
					</view>
					<view class="couponList" v-show="curr==1">
						<view class="item flexRowBetween boxShaow radius10 oh">
							<view class="L">
								<image src="../../static/images/choujiang-icon.png" mode=""></image>
							</view>
							<view class="R">
								<view>15元现金券</view>
								<view class="mny font12 color3">满16元<text class="price font16 ftw">9.00</text></view>
								<view class="flexEnd">
									<view class="btn"  @click="couponXqShow">查看详情</view>
								</view>
							</view>
						</view>
						<view class="item flexRowBetween boxShaow radius10 oh">
							<view class="L">
								<image src="../../static/images/stores_order-img.png" mode=""></image>
							</view>
							<view class="R">
								<view>15元现金券</view>
								<view class="mny font12 color3">满16元<text class="price font16 ftw">9.00</text></view>
								<view class="flexEnd">
									<view class="btn"  @click="couponXqShow">查看详情</view>
								</view>
							</view>
						</view>
					</view>
				</view>
				<view class="pdtb10 borderB1 seltList">
					<view class="flex one">	
						<view class="L-icon"><image src="../../static/images/stores_order-icon3.png" mode=""></image></view>
						<view class="tex font13 avoidOverflow">充值500元，送价值108元券</view>
						<view class="xqBtn" :class="curr==2?'on':''" @click="openXqBtn('2')"><view class="btn">详情</view></view>
						<view class="seltBtn flexEnd">
							<image class="icon" src="../../static/images/address-icon1.png" mode=""></image>
						</view>
					</view>
					<view class="couponList" v-show="curr==2">
						<view class="item flexRowBetween boxShaow radius10 oh">
							<view class="L">
								<image src="../../static/images/choujiang-icon.png" mode=""></image>
							</view>
							<view class="R">
								<view>15元现金券</view>
								<view class="mny font12 color3">满16元<text class="price font16 ftw">9.00</text></view>
								<view class="flexEnd">
									<view class="btn"  @click="couponXqShow">查看详情</view>
								</view>
							</view>
						</view>
						<view class="item flexRowBetween boxShaow radius10 oh">
							<view class="L">
								<image src="../../static/images/stores_order-img.png" mode=""></image>
							</view>
							<view class="R">
								<view>15元现金券</view>
								<view class="mny font12 color3">满16元<text class="price font16 ftw">9.00</text></view>
								<view class="flexEnd">
									<view class="btn"  @click="couponXqShow">查看详情</view>
								</view>
							</view>
						</view>
					</view>
				</view>
				<view class="pdtb10 borderB1 seltList">
					<view class="flex one">	
						<view class="L-icon"><image src="../../static/images/stores_order-icon3.png" mode=""></image></view>
						<view class="tex font13 avoidOverflow">充值800元，送价值156元券</view>
						<view class="xqBtn" :class="curr==3?'on':''" @click="openXqBtn('3')"><view class="btn">详情</view></view>
						<view class="seltBtn flexEnd">
							<image class="icon" src="../../static/images/address-icon1.png" mode=""></image>
						</view>
					</view>
					<view class="couponList" v-show="curr==3">
						<view class="item flexRowBetween boxShaow radius10 oh">
							<view class="L">
								<image src="../../static/images/choujiang-icon.png" mode=""></image>
							</view>
							<view class="R">
								<view>15元现金券</view>
								<view class="mny font12 color3">满16元<text class="price font16 ftw">9.00</text></view>
								<view class="flexEnd">
									<view class="btn"  @click="couponXqShow">查看详情</view>
								</view>
							</view>
						</view>
						<view class="item flexRowBetween boxShaow radius10 oh">
							<view class="L">
								<image src="../../static/images/stores_order-img.png" mode=""></image>
							</view>
							<view class="R">
								<view>15元现金券</view>
								<view class="mny font12 color3">满16元<text class="price font16 ftw">9.00</text></view>
								<view class="flexEnd">
									<view class="btn"  @click="couponXqShow">查看详情</view>
								</view>
							</view>
						</view>
					</view>
				</view>
				<view class="pdtb10 borderB1 seltList">
					<view class="flex one">	
						<view class="L-icon"><image src="../../static/images/stores_order-icon3.png" mode=""></image></view>
						<view class="tex font13 avoidOverflow">暂不充值</view>
						<view class="xqBtn"></view>
						<view class="seltBtn flexEnd">
							<image class="icon" src="../../static/images/address-icon.png" mode=""></image>
						</view>
					</view>
				</view>
			</view>
		</view>
		
		<view class="f5H5"></view>
		<view class="pdlr4">
			<view class="borderB1">
				<view class="ftw pdt10 pdb5 flexRowBetween">
					<view>预约自提时间</view>
					<view class="flexEnd">
						<image class="arrowR" src="../../static/images/about-icon7.png" mode=""></image>
					</view>
				</view>
				<view class="font12 pdb10">约11:05</view>
			</view>
			<view class="borderB1">
				<view class="ftw pdt10 pdb5 flexRowBetween">
					<view>手机号码</view>
					<view class="flexEnd">
						<image class="arrowR" src="../../static/images/about-icon7.png" mode=""></image>
					</view>
				</view>
				<view class="font12 pdb10">15623231102</view>
			</view>
			<view class="borderB1">
				<view class="ftw pdt10 pdb5 flexRowBetween">
					<view>餐具分数</view>
					<view class="flexEnd">
						<image class="arrowR" src="../../static/images/about-icon7.png" mode=""></image>
					</view>
				</view>
				<view class="font12 pdb10 color3">请选择餐具分数</view>
			</view>
			<view class="borderB1">
				<view class="ftw pdt10 pdb5 flexRowBetween">
					<view>备注信息</view>
					<view class="flexEnd">
						<image class="arrowR" src="../../static/images/about-icon7.png" mode=""></image>
					</view>
				</view>
				<view class="font12 pdb10 color3">请输入最多50字的憋住信息(如需发票请扫描小票二维码)</view>
			</view>
		</view>
		
		
		<!-- 底部菜单按钮 -->
		<view class="xqbotomBar">
			<view class="twoNav center w flex">
				<view class="item L flexCenter">
					<view class="white font12 flex">总计：<view class="price font13">36</view></view>
				</view>
				<view class="item R flexCenter" >
					<view class="white">微信支付</view>
				</view>
			</view>
		</view>
		
		<view class="black-bj" v-show="is_show"></view>
		
		<!-- 选择优惠券弹框 -->
		<view class="couponShow_alert" v-show="is_couponShow_alert">
			<view class="Ttit flexRowBetween pdlr4 f5bj">
				<view>选择优惠券</view>
				<view @click="couponShow_alert">取消</view>
			</view>
			<view class="infor">
				<view class="lis">无可用的优惠券</view>
				<view class="lis">无可用的优惠券</view>
			</view>
		</view>
		
		<!-- 优惠券详情弹框 -->
		<view class="couponXqShow radius10" v-show="is_couponXqShow">
			<view class="closebtn font20" @click="couponXqShow">×</view>
			<view class="Ttit center pdlr4 borderB1">
				<view>优惠券详情</view>
			</view>
			<view class="cont pdlr4 font12">
				<view class="item flexRowBetween">
					<view class="ll">显示说明</view>
					<view class="rr">使用小程序点单</view>
				</view>
				<view class="item flexRowBetween">
					<view class="ll">有效时间</view>
					<view class="rr">2019-09-18至2019-10-18</view>
				</view>
				<view class="item flexRowBetween">
					<view class="ll">可用时段</view>
					<view class="rr">周一至周日</view>
				</view>
				<view class="item flexRowBetween">
					<view class="ll">使用须知</view>
					<view class="rr">领券成功后，在小程序点单内容在小程序点单内容，自有效期领券之日起90天内，可与其他优惠同享。</view>
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
				is_show:false,
				specsListDate:[{},{},{}],
				currSpecs:0,
				is_coupon:false,
				curr:0,
				is_couponShow_alert:false,
				is_couponXqShow:false
			}
		},

		onLoad(options) {
			// uni.setStorageSync('canClick', true);
		},

		onShow() {
			const self = this;
			document.title = '提交订单'
		},

		methods: {
			changeSpecs(index){
				const self = this;
				self.currSpecs = index
			},
			openXqBtn(curr){
				const self = this;
				if(curr!=self.curr){
					self.curr = curr
				}
			},
			couponShow_alert(){
				const self = this;
				self.is_show = !self.is_show
				self.is_couponShow_alert = !self.is_couponShow_alert
			},
			couponXqShow(){
				const self = this;
				self.is_show = !self.is_show
				self.is_couponXqShow = !self.is_couponXqShow
			},
			getMainData() {
				const self = this;
				console.log('852369')
				const postData = {};
				postData.tokenFuncName = 'getProjectToken';
				self.$apis.orderGet(postData, callback);
			},
		}
	}
</script>

<style>
	@import "../../assets/style/coupon.css";
	@import "../../assets/style/prodctDetail.css";
	page{padding-bottom:140rpx;}
	
	.xqbotomBar{z-index: 90;}
	
	.selt_list{padding-bottom: 10rpx;}
	.selt_list .item{padding-bottom: 10rpx;}
	.selt_tit{margin-right: 20rpx;}
	
	.specsIndex{flex-wrap: wrap;align-items: flex-start;}
	.specsIndex .item{width: 210rpx;  height: 250rpx; border: 2rpx solid #eee;border-radius: 10rpx;overflow: hidden;margin-right: 30rpx;box-sizing: border-box;margin:0 30rpx 30rpx 0;}
	.specsIndex .item:nth-of-type(3n){margin-right: 0;}
	.specsIndex .item .pic{ width: 152rpx; height: 112rpx; display: block; margin: 20rpx auto;}
	.specsIndex .numBox .redBj{background: #DA251C; color: #fff;}
	.fxNum{min-width: 30rpx; height:30rpx; line-height: 30rpx;border-radius: 30rpx;background: #DA251C; color: #fff; font-size: 24rpx; position: absolute; top: 10rpx;right: 10rpx; display: none;}
	.fxDelt{width: 36rpx; height: 36rpx; line-height: 32rpx;border-radius: 30rpx;background: #DA251C; color: #fff;font-size: 40rpx;position: absolute; bottom: 10rpx;right: 10rpx; display: none;}
	.specsIndex .item.on{border: 2rpx solid #DA251C;}
	.specsIndex .item.on .fxNum,.specsIndex .item.on .fxDelt{ display: block;}
	
	.seltCoupon .one .L-icon{width: 24rpx; height: 30rpx; display: block; margin-right: 10rpx;}
	.seltCoupon .one .L-icon image{width: 100%; height: 100%; display: block;}
	.seltCoupon .one .tex{width: 400rpx;font-size: 26rpx;}
	.seltCoupon .one .xqBtn{width: 100rpx;margin: 0 20rpx ;}
	.seltCoupon .one .xqBtn .btn{width: 100%; height: 40rpx; line-height: 40rpx;text-align: center;color: #666;font-size: 24rpx;border-radius: 30rpx;border: 2rpx solid #eee;}
	.seltCoupon .one .seltBtn{width: 100rpx; }
	.seltCoupon .one .seltBtn .icon{width: 40rpx; height: 40rpx; display: block;}
	
	/* 优惠券弹框 */
	.couponShow_alert{background: #fff;position: fixed; bottom: 0; left: 0; width: 100%;box-sizing: border-box; z-index: 90;}
	.couponShow_alert .Ttit{ line-height: 80rpx;}
	.couponShow_alert .infor{padding: 30rpx 4%;}
	.couponShow_alert .infor .lis{margin-bottom: 30rpx; width: 100%;line-height: 70rpx;padding: 0 20rpx;box-sizing: border-box; border: 2rpx solid #eee;}
	
	/* 优惠券详情弹框 */
	.couponXqShow{ width: 80%; background: #fff;position: fixed; top: 50%; left: 50%; transform: translate(-50%,-50%);box-sizing: border-box; z-index: 90;}
	.couponXqShow .Ttit{ line-height: 80rpx;}
	.couponXqShow .cont{min-height: 600rpx;overflow-y: auto; line-height: 40rpx;}
	.couponXqShow .cont .item{padding-top: 30rpx;align-items: flex-start;}
	.couponXqShow .cont .ll{width: 25%; color: #666;}
	.couponXqShow .cont .rr{width: 75%;}
</style>
