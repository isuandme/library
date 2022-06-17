<template>
	<view class="thumb_item">
		<view class="thumb_top">
			<image :src="(`${news.otherImg}`)" mode=""></image>
			<view class="name_wrap">
				<view class="name">
					{{news.otherName}}
				</view>
				<view class="date">
					{{news.date}}
				</view>
			</view>
		</view>
		<view class="thumb_tip">
			<!-- 评论回复 -->
			<view class="" v-show="news.status === 'comments_replay' ">
				回复<text>{{news.replyName}}：</text>{{news.replyContent}}
			</view>
			<!-- 评论 -->
			<view class="" v-show="news.status === 'comments' ">
				{{news.commentContent}}
			</view>
			<!-- 点赞 -->
			<view class="" v-show="news.status === 'thumb_comment' ||news.status === 'thumb_blog'">
				{{news.thumbTip}}
			</view>
		</view>
		<view class="thumb_bottom">
			<!-- 点赞评论 | 回复评论 -->
			<view class="thumb_comment" v-show="news.status == 'comments_replay' || news.status == 'thumb_comment'">
				<view class="name"  v-show="news.status == 'comments_replay' || news.status == 'thumb_comment'">
					{{news.commentName}}：
				</view>
				<view class="comments_content"  v-show="news.status == 'comments_replay' || news.status == 'thumb_comment'">
					{{news.commentContent}}
				</view>
			</view>
			<view class="comments_essay">
				<image  :src="(`${news.bloggerImg}`)" mode=""></image>
				<view class="name_wrap">
					<view class="name">
						{{news.bloggerName}}
					</view>
					<view class="content">
						{{news.blogContent}}
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"news_card",
		props:{
			news: {
				type: Object,
			},
		},
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss">
	
	.thumb_item{
		margin: 20rpx 10rpx; 
		padding: 10rpx;
		background-color: #fff;
		.thumb_top{
			display: flex;
			image{
				width: 100rpx;
				height: 100rpx;
				margin: 0 10rpx;
			}
			.name_wrap{
				display: flex;
				flex-direction: column;
				margin-top: 15rpx;
				.name{
					
				}
				.date{
					font-size: 25rpx;
					color: gray;
				}
			}
		}
		.thumb_tip{
			margin: 20rpx;
			color: #414141;
			line-height: 50rpx;
			text{
				margin-left: 5rpx;
				color: #e3ac64;
			}
		}
		.thumb_bottom{
			padding: 20rpx;
			background-color: #f8f8f8;
			.thumb_comment{
				display: flex;
				.name{
					color: #e3ac64;
				}
				.comments_content{
					color: gray;
					width: 400rpx;
					color: gray;
					overflow: hidden;
					text-overflow: ellipsis;    
					white-space: nowrap;
				}
			}
			.comments_essay{
				background-color: #fff;
				margin: 20rpx 0;
				padding: 10rpx 0;
				display: flex;
				image{
					width: 150rpx;
					height: 150rpx;
				}
				.name_wrap{
					display: flex;
					flex-direction: column;
					margin-top: 20rpx;
					margin-left: 10rpx;
					.name{
						
					}
					.content{
						width: 500rpx;
						margin-top: 20rpx;
						color: gray;
						overflow: hidden;
						text-overflow: ellipsis;    
						white-space: nowrap;
					}
				}
			}
		}
	}
</style>