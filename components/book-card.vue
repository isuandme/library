<template>
	<view class="hot_item">
		<image class="img" :src="(`${bookInfo.imgPath}`)" mode=""></image>
		<view class="book_info">
			<view class="book_name">{{bookInfo.name}}</view>
			<view class="book_author">{{bookInfo.author}}</view>
			<view class="tag">
				<text>{{bookInfo.detail.year}} |</text>
				<text>{{bookInfo.detail.type}} |</text>
				<text>{{bookInfo.detail.press}}</text>
			</view>
			<view class="hot_tag_wrap">
				<!-- <view>
					TOP1<text> 借阅次数{{bookInfo.lendCount}}K</text>
				</view> -->
				<slot></slot>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"book-card",
		props:{
			bookInfo:{
				type:Object
			}
		},
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss">
.hot_item{
	box-sizing: border-box;
	padding: 10rpx;
	margin: 10rpx auto;
	display: flex;
	width: 100%;
	background-color: #fff;
	border-bottom: 1px solid #d8d8d8;
	image{
		flex: 3;
		margin: 10rpx;
		height: 200rpx;  //230
		width: 100%;
	}
	.book_info{
		flex: 7;
		margin-left: 25rpx;
		.book_name{
			font-size: 35rpx;
			font-weight: 700;
		}
		.book_author{
			color: #767676;
		}
		text{
			color: #767676;
			font-size: 25rpx;
			padding-right: 5rpx;
		}
		// .hot_tag_wrap{
		//     view{
		//     	display: inline-block;
		//     	font-size: 25rpx;
		//     	color: #fff;
		//     	padding: 5rpx 15rpx;
		//     	border-radius: 15rpx;
		//     	background: linear-gradient(130deg,red,orange);
		//     	margin-top: 20rpx;
		//     	text{
		//     		color: #565656;
		//     		font-size: 20rpx;
		//     		margin-left: 10rpx;
		//     	}
		//     }
		// }
	}
}
</style>