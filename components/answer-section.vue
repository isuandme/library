<template>
	<view class="answer_wrap">
		<view class="answer_wrap">
			<view class="top">
				评论 {{answerList.total}}
			</view>
			<!-- <view class="writeComments">
				<image :src="(`${answerList.myImgPath}`)" mode=""></image>
				<u--input class='input' :fontSize="25" type="text" placeholder="写下你的评论"></u--input>
			</view> -->
			<view class="comments_wrap">
				<view class="comments_item" v-for="(item,index) in answerList.comments " :key="index">
					<image :src="(`${item.imgPath}`)" mode=""></image>
					<view class="info_wrap">
						<view class="name">
							{{item.name}}
						</view>
						<view class="comments_content">
							{{item.content}}
						</view>
						<view class="bottom">
							<view class="left">
								{{item.date}}
							</view>
							<view class="right">
								<uni-icons class="icon" type="chat" color="#595959" size="18" />
								<uni-icons class="icon" type="hand-up" color="#595959" size="18" />
								<text>{{item.thumbUp}}</text>
							</view>
						</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"answer-section",
		props: {
			answerList: {
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
.answer_wrap{
	.answer_wrap{
		margin: 10rpx;
		.top{
			margin-left:20rpx;
			margin-bottom: 20rpx;
		}
		.writeComments{
			margin: 20rpx;
			margin-left: 10rpx;
			display: flex;
			image{
				width: 70rpx;
				height: 70rpx;
				margin-right: 10rpx;
			}
			.input{
				width: 500rpx;
			}
			
		}
		.comments_wrap{
			.comments_item{
				display: flex;
				image{
					width: 70rpx;
					height: 70rpx;
					margin: 0 10rpx;
				}
				.info_wrap{
					display: flex;
					flex-direction: column;
					width: 600rpx;
					margin-top: 20rpx;
					.name{
						font-weight: 700;
						
					}
					.comments_content{
						font-size: 30rpx;
						line-height: 45rpx;
					}
					.bottom{
						display: flex;
						justify-content: space-between;
						font-size: 25rpx;
						width: 100%;
						color: gray;
						margin-top: 15rpx;
						.left{
							
						}
						.right{
							.icon{
								margin-left: 50rpx;
							}
							text{
								margin-left: 10rpx;
							}
						}
					}
				}
			}
		}
	}
}
</style>