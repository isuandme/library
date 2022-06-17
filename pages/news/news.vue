<template>
	<view class="news">
		<input type="text" placeholder="搜索" disabled>
		<view class="about">
			<view class="about_me" @click="goAiteMe">
				<view class="img">
					<text class="iconfont icon-aite"></text>
				</view>
				<view class="text">
					@我的
				</view>
				<view class="icon">
					<uni-icons type="right" color="#666" size="18" />
				</view>
			</view>
			<view class="about_me" @click="goComments">
				<view class="img">
					<text class="iconfont icon-xiaoxi"></text>
				</view>
				<view class="text">
					评论
				</view>
				<view class="icon">
					<uni-icons type="right" color="#666" size="18" />
				</view>
			</view>
			<view class="about_me" @click="goThumbUp">
				<view class="img">
					<text class="iconfont icon-zan"></text>
				</view>
				<view class="text">
					赞
				</view>
				<view class="icon">
					<uni-icons type="right" color="#666" size="18" />
				</view>
			</view>
		</view>
		<view class="news_wrap">
			<view class="news_item" v-for="(item,index) in [1,1,1,1,1,1,1,11,1]" :key="index">
				<image src="https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500" mode=""></image>
				<view class="name_news">
					<view class="name">
						王一博
					</view>
					<view class="content">
						感谢你的关注感谢你的关注感谢你的关注感谢你的关注感谢你的关注感
					</view>
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
			goAiteMe(){
				uni.navigateTo({
					url:'../aite/aite'
				})
			},
			goComments(){
				uni.navigateTo({
					url:'../comments/comments'
				})
			},
			goThumbUp(){
				uni.navigateTo({
					url:'../thumbUp/thumbUp'
				})
			}
		}
	}
</script>

<style lang="scss">
.news{
	input{
		margin: 20rpx;
		padding: 10rpx 20rpx;
		background-color: #eee;
		border-radius: 25rpx;
		font-size: 25rpx;
	}
	.about{
		.about_me{
			margin: 10rpx 20rpx;
			padding: 20rpx 0;
			border-bottom: 1px solid #eee;
			.img{
				display: inline-block;
				background-color: #e7754c;
				padding: 20rpx;
				border-radius: 50%;
				.iconfont{
					color: #fff;
					font-size: 50rpx;
				}
			}
			.text{
				vertical-align: middle;
				display: inline-block;
				margin: 0 30rpx;
			}
			.icon{
				float: right;
				margin: 30rpx 10rpx;
			}
		}
		.about_me:nth-child(2){
			.img{
				background-color: #1cab1c;
			}
		}
		.about_me:nth-child(3){
			.img{
				background-color: #4c9fc5;
			}
		}
	}
	.news_wrap{
		margin: 0 20rpx;
		.news_item{
			margin: 10rpx 0;
			padding: 20rpx 0;
			border-bottom: 1px solid #eee;
			display: flex;
			image{
				width: 100rpx;
				height: 100rpx;
				margin-right: 20rpx;
			}
			.name_news{
				display: flex;
				flex-direction: column;
				margin-top: 10rpx;
				.name{
					margin-bottom: 10rpx;
				}
				.content{
					width: 550rpx;
					color: gray;
					font-size: 25rpx;
					overflow: hidden;
					text-overflow: ellipsis;    
					white-space: nowrap;
				}
			}
		}
	}
}
</style>
