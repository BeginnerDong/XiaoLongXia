<template>
	<view>
		<view class="sethead pubBj center white">
			<view class="tex fs13">剩余点数</view>
			<view class="number">0</view>
		</view>
		
		<view class="pdlr4">
			<view class="tit_xian pr"><view class="center tt font15">集点说明</view></view>
			<view class="msgTex color2 font13">
				<view class="child flex">
					<view class="tit">加点：</view>
					<view class="text">下单金额每满100点加1点，剩余部分不足100则不参与加点</view>
				</view>
				<view class="child flex">
					<view class="tit">扣点：</view>
					<view class="text">退单金额每满100点加1点，剩余部分不足100则不参与加点</view>
				</view>
			</view>
			
			<view class="tit_xian pr"><view class="center tt font15">集点明细</view></view>
			<view class="detal_table center">
				<view class="tHead tr flex font14">
					<view class="th">时间</view>
					<view class="th">点数</view>
					<view class="th">说明</view>
				</view>
				<view class="tbody tr flex font13 color2" v-for="(item,index) in tableDate" :key="index">
					<view class="td">2019-10-17</view>
					<view class="td">5</view>
					<view class="td">加点</view>
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
				tableDate:[{},{},{}]
			}
		},

		onLoad(options) {
			uni.setStorageSync('canClick', true);
		},

		onShow() {
			const self = this;
			document.title = '集点明细'
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
	 page{padding-bottom: 60rpx;}
	.sethead{width: 100%; height: 300rpx;box-sizing: border-box; padding: 70rpx 4%;}
	.sethead .tex{ font-size: 26rpx; margin-bottom: 20rpx;}
	.sethead .number{font-size: 100rpx;}
	.tit_xian{width: 100%; height: 2rpx;background: #DA251C; margin: 50rpx auto;}
	.tit_xian .tt{line-height: 40rpx;width: 166rpx;background: #fff;margin: 0 auto;position: absolute; top: 50%;left: 50%;transform: translate(-50%,-50%);}
	
	.msgTex .child{align-items: initial;padding-bottom: 30rpx; line-height: 40rpx;}
	.msgTex .tit{width: 90rpx;}
	.msgTex .text{width: 600rpx;}
	
	.detal_table .th,.detal_table .td{width: 33.3%;box-sizing: border-box;padding: 12rpx 10rpx;}
</style>
