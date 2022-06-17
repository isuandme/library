<template>
	<view class="recommend">
		<view class="topTitle">
			为为什么会突然放弃了一个自己喜欢了很久的人？？
		</view>
		<view class="askman">
			<image src="https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500" mode=""></image>
			<view class="name_wrap">
			     <view class="name">
			     	巧克力田田
			     </view>
				 <view class="about">
				 	2021新知答主
				 </view>
			</view>
			<view class="follow">
				+关注
			</view>
		</view>
		<view class="content">
			利用空闲时间看了《历史选择了毛泽东》，让我再看了《觉醒年代》的基础上更加了解中国共产党的发展历史，很显然不是什么事情都是一帆风顺的，在中国共产党成立之后，在陈独秀同志因右倾错误被开除党籍之后，到1935年遵义会议之前，走马灯似的换了六个领袖，即陈独秀、瞿秋白、向忠发、李立三、王明、博古，经历了一右三“左”(即陈独秀的右倾和瞿秋白、李立三、王明与博古的三次“左”倾)。直至遵义会议，才确立了毛泽东的领袖地位。这一路走来，见证了中国共产党的起起伏伏，见证了革命根据地一个个的建立，见证了红军的一步步壮大。
			本书前一部分写了在毛泽东以前的中共领袖史，描述了历史对他们的走马灯般的淘汰。如列宁所说︰“他们当领袖是不合格的，看来他们在革命期间将不得不由领袖变为下屈，否则就会被抛弃。”中间一部分描写秋收起义失败后毛泽东在井冈山建立革命根据地后展现出的军事才能，这其中从以第一次反围剿到第五次反围剿无一不展示出毛泽东卓越的军事政治才能。到了最后部分重点描述从遵义会议确立毛泽东的领袖地位之后，面临张国焘和王明两次严重的挑战，直至中共“七大”把毛泽东思想作为指导方针写入中共党章。
			其实整本书看下来，大多数人都犯过错，就连毛泽东也不例外，本书也描写了毛泽东亲口承认自己的错误有真错有假错，但不一样的是最后没有走上革命道路的人，意识不到自己的真错，“知错就改，善莫大焉”，正是由于伟人能够从错误中总结经验和教训，才能带领中国共产党走向正确的道路。
			中间的部分就是本书的核心，即详细介绍了历史如何选择了毛泽东。从八七会议写起，写井冈山的斗争，写红都瑞金的艰难岁月﹐写长征中血的教训，写遵义城里那场举世闻名的会议。正所谓︰“天将降大任于斯人也，必先苦其心志，劳其筋骨，饿其体肤，空乏其身，行拂乱其所为。”在这些日子里，毛泽东也曾经几度被撤职,几度遭批判，一次被捕，几番病重。在其中我看到了毛泽东坚忍不拔的心，不管按了多少莫须有的罪名他也依旧保持初心，不论多少次撤职甚至有人错误传达要开除他党籍的时候他都没有放弃，正是在这历史的角逐之中，毛泽东以其正确的思想、策略和路线，脱颖而出，一跃而为中共领袖，从此领导中共达四十一年之久。作者以其翔实、流畅的笔调，并以崭新的、特殊的“领袖史”视角，写出了毛泽东被选择作为中国共产党领袖的历史必然性，刻画了毛泽东当年的沉浮，并披露了许多鲜为人知的
		</view>
		<answer-section :answerList="answerList"></answer-section>
		<view class="bottom_bar">
			<input type="text" placeholder="说点什么吧~">
			<view class="icon_wrap">
				<view class="icon_item">
					<uni-icons class="icon" type="heart" color="#595959" size="20" />
					<view class="amount">
						12
					</view>
				</view>
				<view class="icon_item">
					<uni-icons class="icon" type="star" color="#595959" size="20" />
					<view class="amount">
						12
					</view>
				</view>
				<view class="icon_item">
					<uni-icons class="icon" type="chatbubble" color="#595959" size="20" />
					<view class="amount">
						12
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
import answerSection from "../../components/answer-section.vue"
	export default {
		components: {
			answerSection
		},
		data() {
			return {
				answerList:{
					total:3,
					myImgPath:'https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500',
					comments:[
						{
							imgPath:'https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500',
							name:'田田',
							content:'太真实了吧！！！',
							date:'2022-5-19',
							thumbUp:25
						},{
							imgPath:'https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500',
							name:'百香果',
							content:'太真实了吧！！！',
							date:'2022-5-19',
							thumbUp:25
						},{
							imgPath:'https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500',
							name:'巴西龟',
							content:'太真实了吧！！！',
							date:'2022-5-19',
							thumbUp:25
						},{
							imgPath:'https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500',
							name:'不锈钢',
							content:'啊啊啊啊啊啊啊啊啊啊！！！',
							date:'2022-5-19',
							thumbUp:25
						},{
							imgPath:'https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500',
							name:'保险杠',
							content:'真情实感！！！',
							date:'2022-5-19',
							thumbUp:25
						},
					]
				}
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
.recommend{
	width: 100%;
	margin: 20rpx 10rpx;
	.topTitle{
		font-size: 38rpx;
		font-weight: 700;
	}
	.askman{
		margin: 15rpx 0;
		display: flex;
		image{
			width: 80rpx;
			height: 80rpx;
			margin: 0 10rpx;
		}
		.name_wrap{
			display: flex;
			flex-direction: column;
			font-size: 30rpx;
			width: 500rpx;
			.name{
				font-weight: 700;
			}
			.about{
				color: gray;
				font-size: 25rpx;
			}
		}
		.follow{
			padding: 18rpx 20rpx;
			border-radius: 15rpx;
			background-color: #eee;
		}
	}
	.content{
		margin: 15rpx;
		line-height: 55rpx;
	}
	.bottom_bar{
		width: 100%;
		// height: 80rpx;
		margin: 20rpx 0;
		position: sticky;
		bottom: 0;
		margin-bottom: 50rpx;
		background-color: #fff;
		padding: 20rpx;
		display: flex;
		justify-content: space-between;
		input{
			width: 350rpx;
			padding: 10rpx 20rpx;
			margin-top: 15rpx;
			font-size: 25rpx;
			background-color: #f3f3f3;
			border-radius: 20rpx;
		}
		.icon_wrap{
			width: 300rpx;
			display: flex;
			.icon_item{
				flex-direction: column;
				text-align: center;
				.icon{
					margin: 0 20rpx;
				}
				.amount{
					font-size: 20rpx;
				}
			}
		}
	}
}
</style>
