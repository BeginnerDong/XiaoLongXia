<template>
	<view>
		<view class="detailxqBan">
			<image style="width: 100%; height: 400rpx; display: block;" src="../../static/images/stores-banner.png" mode=""></image>
		</view>
		
		<view class="pdlr4">
			<view class="specsTit ftw pdt40">小龙虾 (双拼，任选两款)</view>
			<view class="specsIndex flex">
				<view class="item center"  v-for="(item,index) in specsListDate" :key="index">
					<view><image class="pic" src="../../static/images/stores_order-img.png" mode=""></image></view>
					<view class="tit font12">奥尔良鸡翅一对</view>
					<view class="font12">(加购价)</view>
					<view class="numBox">
						<view @click="counter(index,'-')">-</view>
						<view class="num redBj">{{item.count}}</view>
						<view class="redBj" @click="counter(index,'+')">+</view>
					</view>
				</view>
			</view>
			
			<view class="specsTit ftw pdt40">小吃(任选一款)</view>
			<view class="specsIndex flex">
				<view class="item center"  v-for="(item,index) in specsListDate" :key="index">
					<view><image class="pic" src="../../static/images/stores_order-img.png" mode=""></image></view>
					<view class="tit font12">奥尔良鸡翅一对</view>
					<view class="font12">(加购价)</view>
					<view class="numBox">
						<view class="redBj" @click="counter(index,'-')">-</view>
						<view class="num redBj">{{item.count}}</view>
						<view class="redBj" @click="counter(index,'+')">+</view>
					</view>
				</view>
			</view>
			
			<view class="specsTit ftw pdt40">饮品(任选一款)</view>
			<view class="specsIndex flex">
				<view class="item center"  v-for="(item,index) in specsListDate" :key="index">
					<view><image class="pic" src="../../static/images/stores_order-img.png" mode=""></image></view>
					<view class="tit font12">{{item.title}}</view>
					<view class="font12">(加购价)</view>
					<view class="numBox">
						<view @click="counter(index,'-')">-</view>
						<view class="num redBj">{{item.count}}</view>
						<view class="redBj" @click="counter(index,'+')">+</view>
					</view>
				</view>
			</view>
		</view>
		
		
		
		<!-- 底部菜单按钮 -->
		<view class="xqbotomBar">
			<view class="twoNav center w flex">
				<view class="item L flexCenter">
					<view class="price">179</view>
					<view class="white font12 flex yuanJia" style="margin-top: 8rpx;">299</view>
				</view>
				<view class="item R flexCenter" @click="Router.navigateTo({route:{path:'/pages/store/store'}})">
					<view class="white">加入购物车</view>
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
				specsListDate:[
					{title:'奥尔良鸡翅一对',count:'1'},
					{title:'奥尔良鸡翅一对',count:'0'},
					{title:'奥尔良鸡翅一对',count:'0'},
					{title:'奥尔良鸡翅一对',count:'0'},
					{title:'奥尔良鸡翅一对',count:'0'},
				]
			}
		},

		onLoad(options) {
			// uni.setStorageSync('canClick', true);
		},

		onShow() {
			const self = this;
			document.title = '选规格'
		},

		methods: {
			counter(index,type) {
				const self = this;
				if (type == '+') {
					self.specsListDate[index].count++;
				}else{
					if(self.specsListDate[index].count > 1) {
						self.specsListDate[index].count--;
					}
				};
				self.$Utils.setStorageArray('cartData', self.specsListDate[index], 'id', 999);
				self.countTotalPrice();
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
	@import "../../assets/style/prodctDetail.css";
	page{padding-bottom:140rpx;}
	
	.numBox{ width: 100%; display: flex; justify-content: flex-end; margin-top: 20rpx;}
	.numBox view{ width: 30%; height: 50rpx; color: #999; font-size:32rpx ; text-align: center; line-height: 50rpx; background: #F5F5F5; box-sizing: border-box;border-right: 2rpx solid #ddd;}
	.numBox view:last-child{border: 0;}
	.numBox view.num{ width: 40%; color: #333; font-size: 28rpx;}
	.specsIndex{flex-wrap: wrap;align-items: flex-start;}
	.specsIndex .item{width: 210rpx;  height: 290rpx; border: 2rpx solid #eee;border-radius: 10rpx;overflow: hidden;margin-right: 30rpx;box-sizing: border-box;margin-top: 30rpx;}
	.specsIndex .item:nth-of-type(3n){margin-right: 0;}
	.specsIndex .item .pic{ width: 152rpx; height: 112rpx; display: block; margin: 20rpx auto;}
	.specsIndex .numBox .redBj{background: #DA251C; color: #fff;}
</style>
