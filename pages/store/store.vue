<template>
	<view>
		<view class="detailxqBan">
			<image style="width: 100%; height: 400rpx; display: block;" src="../../static/images/stores-banner.png" mode=""></image>
		</view>
		<view class="scrollMsg">
			<image class="icon" src="../../static/images/stores-icon.png" mode=""></image>
			<uni-notice-bar show-icon="false" scrollable="true" single="true" >
				<view class="avoidOverflow">小程序充值消费更优惠</view>
			</uni-notice-bar>
		</view>
		<view class="flexRowBetween" style="align-items: flex-start;">
			<view class="store_LeftNav">
				<view class="item flexColumn center" :class="currNav==1?'on':''" @click="changeNav('1')">
					<view>
						<image class="icon" :src="currNav==1?'../../static/images/stores-icon1.png':'../../static/images/stores-icon12.png'" mode=""></image>
					</view>
					<view class="name font12">爆款推荐</view>
				</view>
				<view class="item flexColumn center"  :class="currNav==2?'on':''" @click="changeNav('2')">
					<view>
						<image class="icon" :src="currNav==2?'../../static/images/stores-icon11.png':'../../static/images/stores-icon2.png'" mode=""></image>
					</view>
					<view class="name font12">超值套餐</view>
				</view>
				<view class="item flexColumn center" :class="currNav==3?'on':''" @click="changeNav('3')">
					<view>
						<image class="icon" :src="currNav==3?'../../static/images/stores-icon10.png':'../../static/images/stores-icon3.png'" mode=""></image>
					</view>
					<view class="name font12">沙拉意面</view>
				</view>
				<view class="item flexColumn center" :class="currNav==4?'on':''" @click="changeNav('4')">
					<view>
						<image class="icon" :src="currNav==4?'../../static/images/stores-icon9.png':'../../static/images/stores-icon4.png'" mode=""></image>
					</view>
					<view class="name font12">一人食</view>
				</view>
				<view class="item flexColumn center" :class="currNav==5?'on':''" @click="changeNav('5')">
					<view>
						<image class="icon" :src="currNav==5?'../../static/images/stores-icon7.png':'../../static/images/stores-icon5.png'" mode=""></image>
					</view>
					<view class="name font12">吮指小吃</view>
				</view>
				<view class="item flexColumn center" :class="currNav==6?'on':''" @click="changeNav('6')">
					<view>
						<image class="icon" :src="currNav==6?'../../static/images/stores-icon8.png':'../../static/images/stores-icon6.png'" mode=""></image>
					</view>
					<view class="name font12">果汁饮品</view>
				</view>
			</view>
			<view class="store_rightCont" style="padding-right: 4%;">
				<view>
					<image style="width: 100%; height: 400rpx; display: block;" src="../../static/images/stores-img.png" alt=""></image>
				</view>
				
				<view class="tit_xian pr" style="background: #E1E1E1; width: 100%;">
					<view class="center tt font15" style="background: #F5F5F5;">爆款TOP</view>
				</view>
				<view class="shopOrder">
					<view class="item boxShaow radius10 pr flex" v-for="(item,index) in proListDate" :key="index">
						<view class="ll" @click="Router.navigateTo({route:{path:'/pages/shopDetail/shopDetail'}})">
							<image class="pic" src="../../static/images/mall-img.png" mode=""></image>
						</view>
						<view class="rr">
							<view class="titile font15 avoidOverflow2">{{item.title}}</view>
							<view class="color3 font12">一次吃到两种小龙小</view>
							<view class="flexRowBetween Bmny">
								<view class="price">{{item.price}}</view>
								<view class="flexEnd">
									<view class="addBtn font14" v-show="item.addBtn" @click="addBtnShow">+</view>
									<view class="numBox" style="position: absolute; right: 0; bottom: 0;"  v-show="item.numBox">
										<view @click="counter(index,'-')">-</view>
										<view class="num">{{item.count}}</view>
										<view @click="counter(index,'+')">+</view>
									</view>
									<view class="buyBtn font12" v-show="item.seltBtn" @click="Router.navigateTo({route:{path:'/pages/store_specs/store_specs'}})">选搭配</view>
								</view>
							</view>
						</view>
					</view>
				</view>
			</view>
		</view>
		
		<!-- 底部菜单按钮 -->
		<view class="xqbotomBar" v-show="is_xqbotomBar">
			<view class="twoNav center w flex">
				<view class="item L flexCenter">
					<view class="pr" style=" margin-right:20rpx;" @click="proselShow">
						<image class="CarIcon" src="../../static/images/stores-icon16.png" mode=""></image>
						<view class="number">1</view>
					</view>
					<view class="white font12 flex">总计：<view class="price font13">36</view></view>
				</view>
				<view class="item R flexCenter" @click="Router.navigateTo({route:{path:'/pages/store_order/store_order'}})">
					<view class="white">去结算</view>
				</view>
			</view>
		</view>
		
		<!-- 未购选商品 -->
		<view class="xqbotomBar" v-show="!is_xqbotomBar">
			<view class="twoNav center w flex">
				<view class="item L flexCenter">
					<view class="pr" style=" margin-right:20rpx;;">
						<image class="CarIcon" src="../../static/images/stores-icon15.png" mode=""></image>
					</view>
					<view class="white font12 ">未购选商品</view>
				</view>
				<view class="item R flexCenter"  style="background: #dadada;">
					<view class="white">去结算</view>
				</view>
			</view>
		</view>
		
		<view class="black-bj" v-show="is_show"></view>
		
		<!-- 已选商品弹框 -->
		<view class="proselShow" v-show="is_proselShow">
			<view class="closebtn" style="left: 20rpx; right: auto;" @click="proselShow">取消</view>
			<view class="deltBtn"  @click="deltShow"><image src="../../static/images/address-icon2.png" mode=""></image></view>
			<view class="center tit f5bj pdlr4">已选商品</view>
			<view class="item flexRowBetween" v-for="(item,index) in proListDate" :key="index">
				<view style="width: 70%;">
					<view class="titile font12 avoidOverflow">{{item.title}}</view>
					<view class="price font13">36</view>
				</view>
				<view style="width:30%">
					<view class="numBox">
						<view @click="counter(index,'-')">-</view>
						<view class="num">{{item.count}}</view>
						<view @click="counter(index,'+')">+</view>
					</view>
				</view>
			</view>
		</view>
		
		<!-- 删除弹框 -->
		<view class="deltShow center" v-show="is_deltShow">
			<view class="cont radius10">
				<view class="tit">提示</view>
				<view class="text font12 color3 borderB1">确认要清空购物车吗？</view>
				<view class="confirmBtn flexRowBetween">
					<view @click="deltShow" >取消</view>
					<view class="pubColor">确定</view>
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
				currNav:1,
				proListDate:[
					{title:'美味大虾一份',price:'28',count:'1',addBtn:true,numBox:false,seltBtn:false},
					{title:'好吃的大闸蟹一份',price:'36',count:'1',addBtn:false,numBox:true,seltBtn:false},
					{title:'襟抱麻辣大虾一份',price:'46',count:'1',addBtn:false,numBox:false,seltBtn:true}
				],
				is_xqbotomBar:false,
				is_proselShow:false,
				is_deltShow:false
			}
		},

		onLoad(options) {
			// uni.setStorageSync('canClick', true);
		},

		onShow() {
			const self = this;
			document.title = '门店'
		},

		methods: {
			changeNav(index){
				const self = this;
				self.currNav = index
			},
			counter(index,type) {
				const self = this;
				if (type == '+') {
					self.proListDate[index].count++;
				}else{
					if(self.proListDate[index].count > 1) {
						self.proListDate[index].count--;
					}
				};
				self.$Utils.setStorageArray('cartData', self.proListDate[index], 'id', 999);
				self.countTotalPrice();
			},
			addBtnShow(){
				const self = this;
				self.is_xqbotomBar=true;
			},
			proselShow(){
				const self = this;
				self.is_show=!self.is_show;
				self.is_proselShow=!self.is_proselShow
			},
			deltShow(){
				const self = this;
				self.is_deltShow=!self.is_deltShow
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
	@import "../../assets/style/shop.css";
	@import "../../assets/style/prodctDetail.css";
	@import "../../assets/style/store.css";
	page{padding-bottom:140rpx;background: #F5F5F5;}
	
	.shopOrder{ max-height:810rpx; overflow-y:auto;}
	.shopOrder .item{margin: 0 0 30rpx 0;}
	.shopOrder .item .rr{width: 280rpx;}
	.shopOrder .item .buyBtn{border-radius: 30rpx;}
	.addBtn{width: 40rpx; height: 40rpx;line-height: 40rpx;text-align: center;color: #fff; background: #DA251C;border-radius: 50%;}
	
	.xqbotomBar{z-index: 90;}
	
	/* 加减数量 */
	.numBox{position:initial; bottom: auto;right: auto;}
	.numBox view.num{border-radius: 0;background: #FFF;color: #222;width: auto;min-width: 30rpx;}
	.numBox view{width: 40rpx; height: 40rpx; line-height: 40rpx;background: #DA251C;color: #FFFFFF;font-size: 28rpx;border-radius: 50%;}
	
</style>
