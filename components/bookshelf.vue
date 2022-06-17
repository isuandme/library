<template>
	<view class="bookshelf">
		<view class="book_top_wrap">
			<view class="left">
				{{bookContent.length}}个收藏夹
			</view>
			<view class="right">
				<view class="down" @click="select">
					{{downList[current]}}
					<uni-icons class="input-uni-icon" :type="isShowDown?'top':'bottom'" size="15" color="#666" />
				</view>
				<view class="down_content" :style="{'height': (height +'rpx')}">
					<view v-for="(item,index) in downList" :key="index"
					:class="current===index?'active':''" class="content_item" @click="change(index)" >
						{{item}}
					</view>
				</view>
				<view class="more" @click="show = true">
					<uni-icons type="more-filled" color="#666" size="18" />
				</view>
				<u-popup :show="show" @close="close" @open="open">
				    <view>
				        <text>出淤泥而不染，濯清涟而不妖</text>
						<button @click="show = false">关闭</button>
				    </view>
					
				</u-popup>
			</view>
		</view>
		<view class="myBookshelf">
			<view class="content_item_wrap" v-for="(item,index) in bookContent" :key="index">
				<view class="bookshelf_item" @click="select2(index)">
					<view class="bookshelf_name_wrap">
						<view class="name">
							{{item.name}}
						</view>
					</view>
					<view class="bookshelf_content_wrap">
						<view class="bookshelf_content_amount">
							{{item.contentAmount}}个内容
						</view>
						<view class="status">
							{{item.contentStatus}}
						</view>
						<view class="icon">
							<uni-icons class="input-uni-icon" :type="item.isShowContent?'top':'bottom'" size="30" color="#666" />
						</view>
					</view>
				</view>
				<view class="content_down" :style="{'height': (item.height +'rpx')}" >
					<view  v-for="(item2,index2) in item.bookInfo" :key="index2" @click="goDetail">
						<book-card :bookInfo="item2">
							<block>
								<view>
									<text> 借阅次数{{item2.lendCount}}K</text>
								</view>
							</block>
						</book-card>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
import BookCard from "@/components/book-card.vue"
	export default {
		components:{
			BookCard
		},
		data() {
			return {
				isShowDown:false,
				height:0,
				current:0,
				downList:['默认排序','按时间','按数量'],
				show:false,
				isShowContent:false,
				height2:0,
				bookContent:[{
					name:'我的书架',
					status:'默认',
					contentAmount:5,
					contentStatus:'公开',
					height:0,
					isShowContent:false,
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
						},
						{
							name:'三体',
							author:'刘慈欣',
							lendCount:4.24,
							imgPath:'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg4.duitang.com%2Fuploads%2Fitem%2F201201%2F17%2F20120117144659_CEEuu.thumb.700_0.jpg&refer=http%3A%2F%2Fimg4.duitang.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1654761703&t=3da0cf622bcd081219c3d8c7ca36877f',
							detail:{
								year:2010,
								type:'长篇小说',
								press:'作家出版社'
							}
						},
						{
							name:'三体',
							author:'刘慈欣',
							lendCount:4.24,
							imgPath:'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg4.duitang.com%2Fuploads%2Fitem%2F201201%2F17%2F20120117144659_CEEuu.thumb.700_0.jpg&refer=http%3A%2F%2Fimg4.duitang.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1654761703&t=3da0cf622bcd081219c3d8c7ca36877f',
							detail:{
								year:2010,
								type:'长篇小说',
								press:'作家出版社'
							}
						},
						{
							name:'三体',
							author:'刘慈欣',
							lendCount:4.24,
							imgPath:'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg4.duitang.com%2Fuploads%2Fitem%2F201201%2F17%2F20120117144659_CEEuu.thumb.700_0.jpg&refer=http%3A%2F%2Fimg4.duitang.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1654761703&t=3da0cf622bcd081219c3d8c7ca36877f',
							detail:{
								year:2010,
								type:'长篇小说',
								press:'作家出版社'
							}
						}
					]
				},
				{
					name:'书架2',
					status:'无',
					contentAmount:2,
					contentStatus:'公开',
					height:0,
					isShowContent:false,
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
				}]
			}
		},
		methods: {
			select(){
				this.isShowDown = !this.isShowDown
				if(this.isShowDown){
					this.height=200;
				}else{
					this.height=0;
				}
			},
			change(i){
				this.current=i;
				this.isShowDown = false ;
				this.height=0;
			},
			select2(i){
				this.bookContent[i].isShowContent = !this.bookContent[i].isShowContent
				if(this.bookContent[i].isShowContent){
					this.bookContent[i].height=255*this.bookContent[i].bookInfo.length ;
				}else{
					this.bookContent[i].height=0 ;
				}
			},
			goDetail(){
				console.log('454564');
				uni.navigateTo({
					url:'../book_detail/book_detail'
				})
			}
		}
	}
</script>

<style lang="scss">
.bookshelf{
	padding: 5rpx 30rpx;
	.book_top_wrap{
		padding: 20rpx 0;
		// border-bottom: 1px solid #eee;
		font-size: 28rpx;
		color: #666;
		display:flex;
		justify-content: space-between;
		.left{
			
		}
		.right{
			display:flex;
			position: relative;
			.down{
				margin-right: 30rpx;
				.input-uni-icon{
					margin-left: 5rpx;
				}
			}
			.down_content{
				z-index: 12;
				position: absolute;
				top: 60rpx;
				left: 0;
				width: 100%;
				background-color: #fff;
				height: 0;
				overflow: hidden;
				transition: all .3s; 
				box-shadow:  0 0 5rpx 1rpx #eee;
				.content_item{
					margin: 20rpx ;
				}
				.active{
					color: coral;
				}
			}
		}
	}
	.myBookshelf{
		margin: 20rpx 0;
		.bookshelf_item{
			border-bottom: 1px solid #d6d6d6;
			padding-bottom: 30rpx;
			margin: 20rpx 0;
			.bookshelf_name_wrap{
				display: flex;
				.name{
					margin-left: 10rpx;
					font-size: 40rpx;
					font-weight: 600;
				}
				.status{
					margin-left: 25rpx;
					margin-top: 10rpx;
					font-size: 25rpx;
					padding: 0 5rpx;
					color: #ff8725;
					border: 1px solid #ff8725;
				}
			}
			.bookshelf_content_wrap{
				margin-top: 30rpx;
				display: flex;
				font-size: 28rpx;
				.bookshelf_content_amount{
					flex: 1;
					margin: 0 30rpx;
				}
				.status{
					flex: 1;
				}
				.icon{
					flex: 2;
					text-align: right;
					margin-top: -20rpx;
					margin-right: 10rpx;
				}
			}
		}
		.content_down{
			// height: 0;
			// overflow: hidden;
			transition: all .5s; 
			overflow: auto;
			margin: 0 15rpx;
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
			.img{
			    height: 235rpx !important;
			}
		}
	}
}
</style>
