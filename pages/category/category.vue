<template>
	<view class="category">
		<view class="nav_bar_top"></view>
		<uni-nav-bar class="category_navbar" leftWidth="0px">
		    <view class="input-view">
		    	<uni-icons class="input-uni-icon" type="search" size="18" color="#999" />
		    	<input confirm-type="search" class="nav-bar-input" type="text" placeholder="输入搜索关键词" disabled
		    		@click="toSearch" />
		    </view>
			<!-- #ifdef APP-PLUS || H5 -->
		    <block slot="right">
		    	<view class="city">
		    		搜索
		    	</view>
		    </block>
			<!-- #endif -->
		</uni-nav-bar>
		<view class="category_wrap">
			<scroll-view scroll-y="true" class="left">
				<view v-for="(item,index) in categoryList" :key="index"
				@click="clickCategory(index)"
				:class="index===currentIndex?'active':''"
				>古典小说</view>
			</scroll-view>
			<scroll-view scroll-y="true" class="right">
				<view class="hot_item_wrap" v-for="(item,index) in bookInfo" :key="index" @click="toDetail">
					<book-card :bookInfo="item">
						<block>
							<view>
								<text> 借阅次数{{item.lendCount}}K</text>
							</view>
						</block>
					</book-card>
				</view>
			</scroll-view>
		</view>
		<!-- #ifdef MP-WEIXIN -->
		   <TabBar :current-page="1" />
		<!-- #endif -->
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
				categoryList:[1,1,1,1,,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],
				currentIndex:0,
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
			}
		},
		methods: {
			clickCategory(i){
				this.currentIndex=i;
			},
			toSearch(){
				uni.navigateTo({
					url:'../search/search'
				})
			},
			toDetail(){
				uni.navigateTo({
					url:'../book_detail/book_detail'
				})
			}
		}
	}
</script>

<style lang="scss">
	page{
		height: 100%;
	}
    .category {
		display: flex;
		// flex-direction: column;
		// align-items: center;
		// justify-content: center;
		height: 100%;
		.nav_bar_top{
			z-index: 10;
			width: 100%;
			height: $uni-topbar-height-sm;
			background-color: #fff;
			position: fixed;
			top: 0;
		}
		.category_navbar{
			z-index: 10;
			position: fixed;
			top: 30px;
			/* #ifdef MP-WEIXIN */
				top: 85rpx;
			/* #endif */
			right: 0;
			width: 100%;
			.city{
				display: flex;
				flex-direction: row;
				align-items: center;
				justify-content: flex-start;
				margin-left: 20rpx;
				flex: 1;
			}
			.input-view{
				background-color: #f8f8f8;
				height: 30px;
				/* #ifdef MP-WEIXIN */
					width: 500rpx;
				/* #endif */
				border-radius: 15px;
				padding: 0 15px;
				margin: 7px 0;
				line-height: 30px;
				/* #ifdef APP-PLUS || H5*/
					flex: 1;
				/* #endif */
				display: flex;
				flex-direction: row;
				align-items: center;
				flex-wrap: nowrap;
				.input-uni-icon{
					margin-right: 20rpx;
				}
				.nav-bar-input{
					width: 100%;
					background-color: #f8f8f8;
				}
				input{
					font-size: 25rpx;
				}
			}
		}
	    .category_wrap{
			display: flex;
			width: 100%;
			margin-top: 140rpx;
			/* #ifdef MP-WEIXIN */
			   margin-top: 168rpx;
			/* #endif */
			.left{
				flex: 1;
				text-align: center;
				border-right: 1px solid #eee;
			    height: 100%;
			    view{
			    	margin: 20rpx 15rpx;
					padding: 15rpx 0;
					border-radius: 5rpx;
			    }
				.active{
					background-color: #ffc072;
					color: #fff;
				}
		    }
			.right{
				flex: 3;
				margin: 0 15rpx;
				// height: 100%;
				.hot_item_wrap{
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
		}
		
	}
</style>
