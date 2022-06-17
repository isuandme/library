<template>
	<view class="overdue">
		<view class="overdue_warp">
			<view class="overdue_item" v-for="(item,index) in [1,1,1]" :key="index">
				<image src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimgservice.suning.cn%2Fuimg1%2Fb2c%2Fimage%2FE2gGKxaAfD1pfE1rRsaJdA.jpg_800w_800h_4e&refer=http%3A%2F%2Fimgservice.suning.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1654761685&t=a3d25d12158e650a790200d1f5d4cb4b" mode=""></image>
			     <view class="center_wrap">
			     	<view class="name">
			     		人间失格
			     	</view>
					<view class="overdue_date">
						已逾期：<text>3</text>天
					</view>
			    </view>
				<view class="right_wrap">
					<image src="http://m.qpic.cn/psc?/V13BrVB31Dch34/ruAMsa53pVQWN7FLK88i5m6AVE3GG3vDEOtPYSLo.74xO0.5txrSAzRg4HGjqTbSc4Ks.uCN.tzBHFOIpvPuZchasdr*RY2wu.*xi3L*.C4!/b&bo=gQCAAIEAgAADByI!&rf=viewer_4" mode=""></image>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
.overdue{
	.overdue_warp{
		 margin: 10rpx 20rpx;
		.overdue_item{
			padding: 20rpx 10rpx;
			display: flex;
			border-bottom: 1px solid #eee;
			image{
				flex: 1.2;
				width: 190rpx;
				height: 190rpx;
				filter: grayscale(100%);
			}
			.center_wrap{
				flex: 2;
				display: flex;
				flex-direction: column;
				margin-top: 50rpx;
				.name{
					font-weight: 700;
					font-size: 33rpx;
				}
				.overdue_date{
					font-size: 25rpx;
					// padding: 8rpx;
					// width: 170rpx;
					border-radius: 15rpx;
					// color: #fff;
					margin-top: 25rpx;
					// background-color: red;
					text{
						font-size: 33rpx;
						font-weight: 700;
						margin-right: 10rpx;
					}
				}
			}
			.right_wrap{
				flex: 1;
				margin-top: 40rpx;
				image{
					width: 120rpx;
					height: 120rpx;
				}
			}
		}
	}
}
</style>
