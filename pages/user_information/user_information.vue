<template>
	<view>
		

		<view class="myInform_Head flexColumn center">
			<view><image class="photo" src="../../static/images/about-img.png" mode=""></image></view>
			<view>哆啦A梦</view>
		</view>
		<view class="f5H5"></view>
		
		<view class="XlineNav pdlr4 whiteBj">
			<view class="item flex" >
				<view class="ll flex">
					<image class="icon" src="../../static/images/gerenxinxi-icon.png"></image>
					<view class="ilblock">姓名</view>
				</view>
				<view class="rr">
					<input type="text" value="" placeholder="请输入姓名" />
				</view>
			</view>
			<view class="item flex">
				<view class="ll flex">
					<image class="icon" src="../../static/images/gerenxinxi-icon1.png"></image>
					<view class="ilblock">性别</view>
				</view>
				<view class="rr">
					<view class="uni-list-cell-db">
						<picker @change="bindPickerChange" :value="index" :range="array">
							<view class="uni-input">{{array[index]}}</view>
						</picker>
					</view>
				</view>
			</view>
			<view class="item flex">
				<view class="ll flex">
					<image class="icon" src="../../static/images/gerenxinxi-icon2.png"></image>
					<view class="ilblock">生日</view>
				</view>
				<view class="rr">
					<input type="text" value="" placeholder="生日信息一旦填写,不允许再次修改哦~" />
				</view>
			</view>
			<view class="item flex">
				<view class="ll flex">
					<image class="icon" src="../../static/images/gerenxinxi-icon3.png"></image>
					<view class="ilblock">手机</view>
				</view>
				<view class="rr">
					<input type="text" value="15623230012" placeholder="填写手机号码" />
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
				showView: false,
				score:'',
				wx_info:{},
				index: 0,
				array:['男','女']
			}
		},
		onLoad() {
			const self = this;
			//self.$Utils.loadAll(['getMainData'], self);
		},
		methods: {
			bindPickerChange(e) {
				// 搜索选择分类
				console.log('picker发送选择改变，携带值为', e.target.value)
				this.index = e.target.value
			},
			getMainData() {
				const self = this;
				console.log('852369')
				const postData = {};
				postData.tokenFuncName = 'getProjectToken';

				const callback = (res) => {
					if (res.solely_code == 100000 && res.info.data[0]) {
						self.mainData = res.info.data;
					} else {
						self.$Utils.showToast(res.msg, 'none')
					};
					self.$Utils.finishFunc('getMainData');

				};
				self.$apis.orderGet(postData, callback);

			},

		},
	};
</script>

<style>
	.myInform_Head{padding:50rpx 4% 40rpx 4%;box-sizing: border-box;}
	.myInform_Head .photo{width: 120rpx;height: 120rpx;border-radius: 50%;margin: 20rpx auto;}
	

	/* 我的-菜单列表 */
	.XlineNav .item{border-bottom: solid 1rpx #eee;box-sizing: border-box;height: 100rpx;font-size: 28rpx;}
	.XlineNav .item:last-child{border-bottom: 0;}
	
	.XlineNav .item .ll .icon{width: 30rpx;height: 30rpx;margin-right: 20rpx; display: block;}
	.XlineNav .item .ll .icon image{height:100%;width: 100%;}
	.XlineNav .item .rr{ width: 80%;padding-left:30rpx;box-sizing: border-box;}
	.XlineNav .item .rr input{width: 100%; height: 40rpx; line-height: 40rpx; display: block;}

</style>
