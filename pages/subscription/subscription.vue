<template>
	<view class="subscription">
		<view class="book_card"  v-for="(item,index) in bookInfo" :key="index" @click="goDetail">
			<book-card :bookInfo="item">
				<block>
					<view>
						<text> 借阅次数{{item.lendCount}}K</text>
					</view>
				</block>
			</book-card>
		</view>
	</view>
</template>

<script>
import BookCard from "../../components/book-card.vue"
	export default {
		components:{
			BookCard
		},
		data() {
			return {
				bookInfo:[
					{
						name:'活着',
						author:'余华',
						lendCount:5.2,
						imgPath:'https://img1.baidu.com/it/u=1275895507,934482785&fm=253&fmt=auto&app=120&f=JPEG?w=459&h=650',
						detail:{
							year:2010,
							type:'长篇小说',
							press:'作家出版社'
						}
					},
					{
						name:'人间失格',
						author:'太宰治',
						lendCount:4.85,
						imgPath:'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimgservice.suning.cn%2Fuimg1%2Fb2c%2Fimage%2FE2gGKxaAfD1pfE1rRsaJdA.jpg_800w_800h_4e&refer=http%3A%2F%2Fimgservice.suning.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1654761685&t=a3d25d12158e650a790200d1f5d4cb4b',
						detail:{
							year:2010,
							type:'长篇小说',
							press:'作家出版社'
						}
					}
				]
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
.subscription{
	.book_card{
		margin: 0 50rpx;
		.img{
		    height: 235rpx !important;
		}
		.hot_tag_wrap{
		    view{
		    	display: inline-block;
		    	font-size: 25rpx;
		    	color: #fff;
				/* #ifdef APP-PLUS */
				   height: 37rpx;
				   line-height: 30rpx;
				/* #endif */
		    	padding: 2rpx 15rpx;
		    	border-radius: 15rpx;
		    	background: linear-gradient(130deg,#ffe353,#f7ffd7);
		    	margin-top: 20rpx;
		    	text{
		    		color: #565656;
		    		font-size: 20rpx;
		    	}
		    }
		}
	}
}
</style>
