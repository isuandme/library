<template>
	<view class="blog_page_wrap">
		<view class="" v-for="(item,index) in blogList" :key="index">
			<blog-card :blogInfo="item"></blog-card>
		</view>
		<view class="tip">
			没有更多了
		</view>
	</view>
</template>

<script>
	import BlogCard from '../../components/blog-card.vue'
	export default {
		components:{
			BlogCard
		},
		data() {
			return {
				blogList:[{
					title:'前端零基础自学：相互监督学习，一起自学找工作！',
					name:'西瓜少年',
					imgPath:'https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500',
					content:'本书前一部分写了在毛泽东以前的中共领袖史，描述了历史对他们的走马灯般的淘汰。如列宁所说︰“他们当领袖是不合格的，看来他们在革命期间将不得不由领袖变为下屈，否则就会被抛弃。”中间一部分描写秋收起义失败后毛泽东在井冈山建立革命根据地后展现出的军事才能，这其中从以第一次反围剿到第五次反围剿无一不展示出毛泽东卓越的军事政治才能。到了最后部分重点描述从遵义会议确立毛泽东的领袖地位之后，面临张国焘和王明两次严重的挑战，直至中共“七大”把毛泽东思想作为指导方针写入中共党章。',
				    thumbUp:122,
					collect:778
				},{
					title:'前端零基础自学：相互监督学习，一起自学找工作！',
					name:'bxiao女孩',
					imgPath:'https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500',
					content:'本书前一部分写了在毛泽东以前的中共领袖史，描述了历史对他们的走马灯般的淘汰。如列宁所说︰“他们当领袖是不合格的，看来他们在革命期间将不得不由领袖变为下屈，否则就会被抛弃。”中间一部分描写秋收起义失败后毛泽东在井冈山建立革命根据地后展现出的军事才能，这其中从以第一次反围剿到第五次反围剿无一不展示出毛泽东卓越的军事政治才能。到了最后部分重点描述从遵义会议确立毛泽东的领袖地位之后，面临张国焘和王明两次严重的挑战，直至中共“七大”把毛泽东思想作为指导方针写入中共党章。',
				    thumbUp:122,
					collect:778
				}
				,{
					title:'前端零基础自学：相互监督学习，一起自学找工作！',
					name:'风声西',
					imgPath:'https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500',
					content:'本书前一部分写了在毛泽东以前的中共领袖史，描述了历史对他们的走马灯般的淘汰。如列宁所说︰“他们当领袖是不合格的，看来他们在革命期间将不得不由领袖变为下屈，否则就会被抛弃。”中间一部分描写秋收起义失败后毛泽东在井冈山建立革命根据地后展现出的军事才能，这其中从以第一次反围剿到第五次反围剿无一不展示出毛泽东卓越的军事政治才能。到了最后部分重点描述从遵义会议确立毛泽东的领袖地位之后，面临张国焘和王明两次严重的挑战，直至中共“七大”把毛泽东思想作为指导方针写入中共党章。',
				    thumbUp:122,
					collect:778
				},{
					title:'前端零基础自学：相互监督学习，一起自学找工作！',
					name:'OKKK',
					imgPath:'https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500',
					content:'本书前一部分写了在毛泽东以前的中共领袖史，描述了历史对他们的走马灯般的淘汰。如列宁所说︰“他们当领袖是不合格的，看来他们在革命期间将不得不由领袖变为下屈，否则就会被抛弃。”中间一部分描写秋收起义失败后毛泽东在井冈山建立革命根据地后展现出的军事才能，这其中从以第一次反围剿到第五次反围剿无一不展示出毛泽东卓越的军事政治才能。到了最后部分重点描述从遵义会议确立毛泽东的领袖地位之后，面临张国焘和王明两次严重的挑战，直至中共“七大”把毛泽东思想作为指导方针写入中共党章。',
				    thumbUp:122,
					collect:778
				},
				]
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
.blog_page_wrap{
	/* margin: 20rpx; */
	height: 100vh;
	overflow: scroll;
	padding: 10rpx;
	width: 100%;
	background-color: #eee;
	.tip{
		text-align: center;
		margin: 50rpx auto;
		color: #9e9e9e;
	}
	
}
</style>
