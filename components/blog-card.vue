<template>
	<view class="recommend_content" @click="goRecommendDetail">
		<view class="content_title">
			{{blogInfo.title}}
		</view>
		<view class="name">
			<image  :src="(`${blogInfo.imgPath}`)" mode=""></image>
			<text>{{blogInfo.name}}</text>
		</view>
		<view class="content">
			{{blogInfo.content}}
		</view>
		<view class="content_bottom">
			<text>{{blogInfo.thumbUp}}赞同</text>
			<text>{{blogInfo.collect}}收藏</text>
		</view>
	</view>
</template>

<script>
	export default {
		name:"blog-card",
		props:{
			blogInfo:{
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
.recommend_content{
			width: 700rpx;
			/* #ifdef MP-WEIXIN */
				width: 100%;
			/* #endif */
			color: gray;
			margin-top: 20rpx;
			background-color: #fff;
			padding: 25rpx 15rpx;
			font-size: 25rpx;
			.content_title{
				color: #000;
				font-size: 30rpx;
				font-weight: 700;
				
			}
			.name{
				margin: 20rpx 5rpx;
				display: flex;
				image{
					width: 60rpx;
					height: 60rpx;
				}
				text{
					margin-left: 15rpx;
					line-height: 55rpx;
				}
			}
			.content{
				display: -webkit-box;
				overflow: hidden;
				text-overflow: ellipsis;
				-webkit-line-clamp: 2;
				-webkit-box-orient: vertical;
				margin-right: 25rpx;
			}
			.content_bottom{
				margin-top: 20rpx;
				text{
					margin-right: 20rpx;
				}
			}
		}
</style>