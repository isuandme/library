<template>
	<view class="thumbUp">
		
		<view class="thumb_wrap">
			<view class="" v-for="(item,index) in newslists" :key="index">
				<news-card :news='item'></news-card>
			</view>
		</view>
	</view>
</template>

<script>
import NewsCard from '../../components/news_card.vue'
	export default {
		components:{
			NewsCard
		},
		data() {
			return {
				newslists:[{
					otherName:'Roseonlydaslp',
					otherImg:'https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500',
					date:'3-9',
					status:'thumb_comment',
					thumbTip:'赞了这条评论',
					commentName:'并肩于',
					commentContent:'对对对对，是这样没错对对对对，是这样没错对对对对，是这样没错',
					bloggerName:'花花好甜啊',
					bloggerImg:'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fup.enterdesk.com%2Fedpic%2Ffd%2Ff1%2Fda%2Ffdf1dacb8ff0b8f13ed29bcbee42f328.jpeg&refer=http%3A%2F%2Fup.enterdesk.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656419838&t=09a36ad23ae5a73d69ad7b2837bfcc08',
					blogContent:'众多组件覆盖开发过程的各个需求，组件功能丰富，多端兼容。让您快速集成，开箱即用'
				},
				{
					otherName:'Roseonlydaslp',
					otherImg:'https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500',
					date:'3-9',
					status:'thumb_blog',
					thumbTip:'赞了这条帖子',
					bloggerName:'什么鬼啊',
					bloggerImg:'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fup.enterdesk.com%2Fedpic%2Ffd%2Ff1%2Fda%2Ffdf1dacb8ff0b8f13ed29bcbee42f328.jpeg&refer=http%3A%2F%2Fup.enterdesk.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656419838&t=09a36ad23ae5a73d69ad7b2837bfcc08',
					blogContent:'众多组件覆盖开发过程的各个需求，组件功能丰富，多端兼容。让您快速集成，开箱即用'
				},
				{
					otherName:'四级必过',
					otherImg:'https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500',
					date:'3-9',
					status:'thumb_comment',
					thumbTip:'赞了这条评论',
					commentName:'1234865',
					commentContent:'宝物啊这是',
					bloggerName:'花花好甜啊',
					bloggerImg:'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fup.enterdesk.com%2Fedpic%2Ffd%2Ff1%2Fda%2Ffdf1dacb8ff0b8f13ed29bcbee42f328.jpeg&refer=http%3A%2F%2Fup.enterdesk.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656419838&t=09a36ad23ae5a73d69ad7b2837bfcc08',
					blogContent:'众多组件覆盖开发过程的各个需求，组件功能丰富，多端兼容。让您快速集成，开箱即用'
				},
				{
					otherName:'Rossssslp',
					otherImg:'https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500',
					date:'3-9',
					status:'thumb_blog',
					thumbTip:'赞了这条帖子',
					bloggerName:'什么鬼啊',
					bloggerImg:'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fup.enterdesk.com%2Fedpic%2Ffd%2Ff1%2Fda%2Ffdf1dacb8ff0b8f13ed29bcbee42f328.jpeg&refer=http%3A%2F%2Fup.enterdesk.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656419838&t=09a36ad23ae5a73d69ad7b2837bfcc08',
					blogContent:'众多组件覆盖开发过程的各个需求，组件功能丰富，多端兼容。让您快速集成，开箱即用'
				}]
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
.thumbUp{
	background-color: #f0f0f0;
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
}
</style>
