<template>
	<view class="" >
		<!--  -->
		<view class="pdlr4 currShop pr flexRowBetween">
			<view style="width: 85%;">
				<view class="item pdt40">您当前选择门店</view>
				<view class="item flex">
					<image class="Licon" src="../../static/images/booking_order-icon.png" mode=""></image>
					<view class="color1 ftw">合成汇店</view>
				</view>
				<view class="item flex">
					<image class="Licon" src="../../static/images/booking_order-icon1.png" mode=""></image>
					<view class="color1 color2">翔因路1003号</view>
				</view>
				<view class="item flex">
					<image class="Licon" src="../../static/images/booking_order-icon2.png" mode=""></image>
					<view class="color1 color2">10:00-22:00</view>
				</view>
				<view class="item flex">
					<image class="Licon" src="../../static/images/booking_order-icon3.png" mode=""></image>
					<view class="color1 color2">021-23536689</view>
				</view>
			</view>
			<view class="flexEnd" style="width: 15%;"><image class="arrowR" src="../../static/images/about-icon7.png" mode=""></image></view>
		</view>
		<view class="f5H5"></view>
		<view class="">
			<view class="pdlr4 pdt40 pdb40">选择日期</view>
		</view>	
		
		<view class="calendar-layer">
			<view class="week-box flexRowBetween">
				<view class="item flex">
					<image class="arrowR" src="../../static/images/booking_order-icon4.png" mode=""></image>
					<view class="tex">上月</view>
				</view>
				<view class="item M font16 center">2019年10月</view>
				<view class="item flexEnd">
					<view class="tex">上月</view>
					<image class="arrowR" src="../../static/images/booking_order-icon5.png" mode=""></image>
				</view>
			</view>
			
			<view class="day-title pdlr4 flexRowBetween">
				<view>日</view>
				<view>一</view>
				<view>二</view>
				<view>三</view>
				<view>四</view>
				<view>五</view>
				<view>六</view>
			</view>
			<view class="pdlr4 dayCont flex">
				<view class="item" :class="[currDay==index?'on':'']" v-for="(item,index) in dayData" :key="index"  @click="chageDay(index)"><span>{{item}}</span></view>
			</view>
			
		</view>
		
		
		<view class="f5H5"></view>
		<view class="pdlr4">
			<view class="pdt40 pdb40">预定信息</view>
			<view class="yudingEdit">
				<view class="item flex">
					<view class="ll" style="width: 100rpx;">时间<text class="red">*</text></view>
					<view class="rr flex"  style="width: 560rpx;">
						<view class="cell-db">
							<picker mode="time" :value="time" start="09:01" end="21:01" @change="bindTimeChangeStart">
								<view class="uni-input">{{time}}</view>
							</picker>
						</view>
						<view style="margin: 0 20rpx;">至</view>
						<view class="cell-db">
							<picker mode="time" :value="time" start="09:01" end="21:01" @change="bindTimeChangeEnd">
								<view class="uni-input">{{timeEnd}}</view>
							</picker>
						</view>
					</view>
				</view>
				<view class="item flex">
					<view class="ll">成人人数<text class="red">*</text></view>
					<view class="rr flex">
						<input type="number" value="" placeholder="选择成人人数" />
					</view>
				</view>
				<view class="item flex">
					<view class="ll">儿童人数<text class="red">*</text></view>
					<view class="rr flex">
						<input type="number" value="" placeholder="选择儿童人数" />
					</view>
				</view>
				<view class="item flex">
					<view class="ll">联系人<text class="red">*</text></view>
					<view class="rr flex">
						<input type="text" value="" placeholder="选输入联系人姓名" />
					</view>
				</view>
				<view class="item flex">
					<view class="ll">手机号码<text class="red">*</text></view>
					<view class="rr flex">
						<input type="text" value="" placeholder="选输入手机号码" />
					</view>
				</view>
				<view class="item flex">
					<view class="ll">特殊要求<text class="red">*</text></view>
					<view class="rr flex">
						<textarea value="" placeholder="输入补充信息" />
					</view>
				</view>
				
			</view>
		</view>
		
		<view class="xqbotomBar">
			<view class="submitbtn w"><button type="button">申请预定</button></view>
		</view>
		
	</view>

</template>

<script>
	export default {
		data() {
			return {
				Router:this.$Router,
				time: '00:00',
				timeEnd:'00:00',
				currDay:0,
				dayData:31
			}
		},

		onLoad(options) {
			uni.setStorageSync('canClick', true);
		},

		onShow() {
			const self = this;
			document.title = '预定订单'
		},
		methods: {
			chageDay(index){
				const self = this;
				self.currDay = index
			},
			bindTimeChangeStart: function(e) {
				this.time = e.target.value
			},
			bindTimeChangeEnd: function(e) {
				this.timeEnd = e.target.value
			},
			getDate(type) {
				const date = new Date();
				let year = date.getFullYear();
				let month = date.getMonth() + 1;
				let day = date.getDate();

				if (type === 'start') {
					year = year - 60;
				} else if (type === 'end') {
					year = year + 2;
				}
				month = month > 9 ? month : '0' + month;;
				day = day > 9 ? day : '0' + day;
				return `${year}-${month}-${day}`;
			},
			getMainData() {
				const self = this;
				self.$apis.userGet(postData, callback);
			}
		}
	}
</script>

<style>
	
	@import "../../assets/style/prodctDetail.css";
	page{padding-bottom: 180rpx;}
	
	.titile{padding: 40rpx 0;}
	.currShop .item{padding-bottom: 30rpx;}
	.currShop .item .Licon{width:30rpx; height: 30rpx; display: block;margin-right: 20rpx;}
	
	.week-box{width: 520rpx;margin: 0 auto 30rpx auto;}
	.week-box .item{width: 20%;}
	.week-box .item.M{width: 60%;}
	.week-box .tex{margin: 0 10rpx; font-size: 24rpx; color: #999;}
	.day-title{line-height: 60rpx;background: #ffedec;}
	.day-title>view{width: 14.2%; text-align: center;}
	.dayCont{flex-wrap: wrap;padding: 30rpx 4%;}
	.dayCont .item{width: 14.2%; text-align: center;}
	.dayCont .item span{width: 56rpx; height: 56rpx; line-height: 56rpx;border-radius: 50%;margin: 10rpx auto; display: block; }
	.dayCont .item.on span{background: #DA251C;color: #fff;}
	
	.yudingEdit .item{padding-bottom: 40rpx; align-items: flex-start;}
	.yudingEdit .item .ll{width: 160rpx; font-size: 26rpx; color: #666; line-height: 60rpx;}
	.yudingEdit .item .rr{width: 520rpx; font-size: 24rpx;}
	.yudingEdit .item .rr input{width: 100%; height: 60rpx; line-height: 60rpx; display: block;box-sizing: border-box;border: 2rpx solid #EEEEEE;padding: 0 20rpx;overflow: hidden; font-size: 24rpx;}
	input::-webkit-input-placeholder{width: 100%;}
	.yudingEdit .item textarea{width: 100%; height: 200rpx; box-sizing: border-box;padding: 20rpx;border: 2rpx solid #EEEEEE;font-size: 24rpx;}
	
	.cell-db{width: 40%; height: 60rpx; line-height: 60rpx; display: block;box-sizing: border-box;border: 2rpx solid #EEEEEE;padding: 0 20rpx;overflow: hidden; font-size: 26rpx; color: #666;}
	
	.xqbotomBar{ height: 140rpx;}
	
</style>
