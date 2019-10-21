<template>
	<view class=" pdt10">
		<view class="xqInfor">
			<view class="center pdb10">标题标题标题标题标题标题标题标题标题</view>
			<view class="cont">
				<view>1、内容内容内容内容内容内容内容内容内容内容 </view>
				<view>2、内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容</view>
				<view>3、内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容 </view>
				<view>4、内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容 </view>
			</view>
		</view>
		
	</view>	

</template>

<script>
	export default {
		data() {
			return {
				Router:this.$Router,
				is_show:false
			}
		},

		onLoad(options) {
			uni.setStorageSync('canClick', true);
		},

		onShow() {
			const self = this;
			document.title = '服务协议'
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
</style>
