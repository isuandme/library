<template>
	<view class="info_bar">
		<view class="info_bar_item"  @click="goBlog">
			<text>{{infoList[0]}}</text>
			<text>发帖</text>
		</view>
		<view class="info_bar_item">
			<text>{{infoList[1]}}</text>
			<text>回答</text>
		</view>
		<view class="info_bar_item" @click="goMyFollows">
			<text>{{infoList[2]}}</text>
			<text>关注</text>
		</view>
		<view class="info_bar_item"  @click="goMyFans">
			<text>{{infoList[3]}}</text>
			<text>粉丝</text>
		</view>
	</view>
</template>

<script>
	export default {
		name:"infoBar",
		props:{
			infoList:{
				type:Array
			}
		},
		data() {
			return {
				
			};
		},
		methods:{
			goMyFollows(){
				uni.navigateTo({
					url:'/pages/myFollows/myFollows'
				})
			},
			goMyFans(){
				uni.navigateTo({
					url:'/pages/Myfans/Myfans'
				})
			},
			goBlog(){
				uni.navigateTo({
					url:'/pages/blog/blog'
				})
			}
		}
	}
</script>

<style lang="scss">
.info_bar{
	// background-color: #fff;
	color: gray;
	display: flex;
	// width: 100%;
	// border-radius: 10rpx;
	padding: 10rpx 0;
	text-align: center;
	padding-top: 30rpx;
	.info_bar_item{
		flex: 1;
		display: flex;
		flex-direction: column;
		margin: 10rpx;
		border-right: 1rpx solid #dcdcdc;
		text{
			align-items: center;
			margin-top: 5rpx;
			font-size: 25rpx
		}
		.iconfont{
			color: #ff924a;
			font-size: 55rpx;
		}
	}
	.info_bar_item:last-child{
		border-right: none;
	}
}
</style>