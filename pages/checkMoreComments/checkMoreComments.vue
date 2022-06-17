<template>
	<view class="check_more_comments">
		<view class="evaluate_item" v-for="(item,index) in [1,1,1,1]" :key="index">
			<view class="evaluate_top">
				<image src="https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500" mode=""></image>
				<view class="name_wrap">
					<text>匿名</text>
					<text>2022-05-09</text>
				</view>
			</view>
			<view class="content">
			     书非常好看，一周看完了，回味无穷！！ 书非常好看，一周看完了，回味无穷！！ 书非常好看，一周看完了，回味无穷！！
		    </view>
			<view class="evaluate_bottom">
				<view class="left">
					浏览 205
				</view>
				<view class="right">
					<uni-icons class="input-uni-icon" type="hand-up" size="18" color="#999" />
					<text>12</text>
					<uni-icons class="input-uni-icon" type="hand-down" size="18" color="#999" />
					<text>0</text>
				</view>
			</view>
		</view>
		<view class="check_more_bottom">
			没有更多了~
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
.check_more_comments{
	margin: 30rpx;
	.evaluate_item{
		border: 1rpx solid #eee;
		padding: 10rpx;
		border-radius: 25rpx;
		margin: 20rpx 0;
		.evaluate_top{
		    display: flex;
			image{
				margin: 0 15rpx;
				width: 75rpx;
				height: 75rpx;
				border-radius: 50%;
			}
			.name_wrap{
				display: flex;
				flex-direction: column;
				font-size: 28rpx;
				margin-top: 5rpx;
				text:first-child{
					
				}
					
				text:last-child{
					font-size: 25rpx;
					color: gray;
				}
			}
		}
		.content{
			font-size: 30rpx;
			margin: 20rpx;
		}
	}
	.evaluate_bottom{
		margin: 20rpx;
		font-size: 25rpx;
		color: #666;
		display: flex;
		justify-content: space-between;
		.left{
			
		}
		.right{
			margin-right: 20rpx;
		}
		.input-uni-icon{
			margin-left: 20rpx;
		}
		text{
			margin-left: 5rpx;
		}
	}
	.check_more_bottom{
		color: #666;
		text-align: center;
		margin: 80rpx 0;
	}
}
</style>
