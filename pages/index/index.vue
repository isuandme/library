<template>
	<view class="home">
		<view class="nav_bar_top"></view>
		
		<!-- #ifdef APP-PLUS || H5 -->
		<uni-nav-bar class="home_navbar">
			    <block slot="left">
			    	<view class="city">
			    		<view>
			    			<text class="uni-nav-bar-text">北京</text>
			    		</view>
			    		<uni-icons type="arrowdown" color="#666" size="18" />
			    	</view>
			    </block>
		     <my-input :text="text"></my-input>
			
		    <block slot="right">
				<view class="city" @click="scan">
					<uni-icons class="input-uni-icon" type="scan" size="30" color="#999" />
				</view>
		    </block>
		</uni-nav-bar>
		<!-- #endif -->
		<!-- #ifdef MP-WEIXIN -->
		<uni-nav-bar class="home_navbar" leftWidth="70rpx">
			
			   <block slot="left">
			   	   <view class="city" @click="scan">
			   	   	   <uni-icons class="input-uni-icon" type="scan" size="25" color="#999" />
			   	   </view>
			   </block>
			 <my-input :text="text"></my-input>
		    <!-- <view class="input-view">
		    	<uni-icons class="input-uni-icon" type="search" size="18" color="#999" />
		    	<input confirm-type="search" class="nav-bar-input" type="text" placeholder="输入搜索关键词" disabled
		    		@click="toSearch" />
		    </view> -->
		</uni-nav-bar>
		<!-- #endif -->
		
		<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000" circular="true" indicator-active-color="#fff">
			<swiper-item v-for=" (index,item) in swiperList" :key="index">
				<image src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fp1.itc.cn%2Fq_70%2Fimages03%2F20220422%2F4452d58683154e3598632ac152530961.jpeg&refer=http%3A%2F%2Fp1.itc.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1654742688&t=1f88524268f90a6d2747475e7882ca81" mode=""></image>
			</swiper-item>
		</swiper>
		<view class="select_position_wrap">
			<view class="position_option"
			v-for="(item,index) in positionList" :key="index"
			:class="index===currentItem?'active':''"
			@click="seletedPosition(index)">
				{{item.position}}
			</view>
			<view class="check_more" @click="goMore">
				查看更多
				<uni-icons type="right" color="#ffffff" size="15" />
			</view>
		</view>
		<view class="detail_scan_warp">
			<view class="count_wrap">
				<view class="count_title">
					读者人数
				</view>
				<view class="count_num">
					{{positionList[currentItem].readingAmount}}
				</view>
			</view>
			<view class="count_wrap">
				<view class="count_title">
					剩余空位数
				</view>
				<view class="count_num">
					{{positionList[currentItem].remainCount}}
				</view>
			</view>
			<progress :percent="amountPercent" activeColor="orange" active stroke-width="18" />
		</view>
		<view class="detail_scan_bottom"></view>
		<view class="mid_bar">
			<view class="borrow_book_wrap" @click="goBorrow">
				<text>自助借书</text>
				<view class="iconfont icon-jieshu">
				</view>
			</view>
			<view class="borrow_book_wrap" @click="goReturn">
				<text>自助还书</text>
				<view class="iconfont icon-woyaohuanshu">
				</view>
			</view>
		</view>
		<view class="hot_title_wrap">
			<view class="hot_title">
				热门推荐
			</view>
		</view>
		<view class="hot_wrap">
			<view class="hot_item_wrap" v-for="(item,index) in bookInfo" :key="index" @click="toDetail">
				<book-card :bookInfo="item">
					<block>
						<view>
							TOP{{index+1}}<text> 借阅次数{{item.lendCount}}K</text>
						</view>
					</block>
				</book-card>
			</view>
		</view>
		<!-- #ifdef MP-WEIXIN -->
		   <TabBar :current-page="0" />
		<!-- #endif -->
	</view>
</template>

<script>
	import BookCard from "../../components/book-card.vue"
	import MyInput from '../../components/input.vue'
	export default {
		components:{
			BookCard,
			MyInput
		},
		data() {
			return {
				swiperList:[1,2,3,4],
				text:'输入关键词搜索',
				// amountPercent:60,
				positionList:[
					{
						position:'1楼A区',
						readingAmount:120,
						remainCount:15
					},
					{
						position:'1楼B区',
						readingAmount:10,
						remainCount:150
					},
					{
						position:'2楼A区',
						readingAmount:100,
						remainCount:19
					},
					{
						position:'2楼B区',
						readingAmount:20,
						remainCount:105
					},
					{
						position:'2楼C区',
						readingAmount:85,
						remainCount:15
					}
				],
				currentItem:0,
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
					}
				]
			}
		},
		computed:{
			amountPercent(){
				return this.positionList[this.currentItem].readingAmount/(this.positionList[this.currentItem].readingAmount+this.positionList[this.currentItem].remainCount)*100;
			}
		},
		onLoad() {

		},
		methods: {
			seletedPosition(i){
				this.currentItem=i;
			},
			toSearch(){
				uni.navigateTo({
					url:'../search/search'
				})
			},
			scan(){
				uni.scanCode({
					success:function(res){
						console.log(res);
						uni.navigateTo({
							url:'../book_detail/book_detail'
						})
					}
				})
			},
			toDetail(){
				uni.navigateTo({
					url:'../book_detail/book_detail'
				})
			},
			goMore(){
				uni.navigateTo({
				})
			},
			goReturn(){
				uni.navigateTo({
					url:'../returnBook/returnBook'
				})
			},
			goBorrow(){
				uni.switchTab({
					url:'../category/category'
				})
			}
		}
	}
</script>

<style lang="scss">
	.home {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		.nav_bar_top{
			z-index: 10;
			width: 100%;
			height: $uni-topbar-height-sm;
			background-color: #fff;
			position: fixed;
			top: 0;
		}
		.home_navbar{
			z-index: 10;
			position: fixed;
			top: 30px;
			/* #ifdef MP-WEIXIN */
				top: 85rpx;
			/* #endif */
			right: 0;
			width: 100%;
			.uni-navbar--border {
			    border-bottom-style: none;
			}
			.city{
				display: flex;
				flex-direction: row;
				align-items: center;
				justify-content: flex-start;
				margin-left: 20rpx;
				/* #ifdef MP-WEIXIN */
					margin-left: 0rpx;
				/* #endif */
				flex: 1;
				.input-uni-icon{
					margin-left: 20rpx;
				}
			}
			.input-view{
				background-color: #f8f8f8;
				height: 30px;
				/* #ifdef MP-WEIXIN */
					width: 420rpx;
				/* #endif */
				border-radius: 15px;
				padding: 0px 15px;
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
	    swiper{
			margin-top: 150rpx;
			/* #ifdef MP-WEIXIN */
				margin-top: 178rpx;
			/* #endif */
			width: 90%;
			height: 350rpx;
			border-radius: 5px;
			overflow: hidden;
			box-shadow: 0 0  10px 5px #ebebeb;
			swiper-item{
				image{
					width: 100%;
				}
			}
		}
		.select_position_wrap{
			margin-top: 20rpx;
			width: 90%;
			display: flex;
			font-size: 25rpx;
			.position_option{
				margin-right: 1rpx;
				padding: 4rpx 8rpx;
				border: 1px solid #313131;
				border-radius: 0 15rpx 0rpx 0;
				border-bottom: none;
				transition: all .4s;
			}
			.active{
				background-color: #FF6B00;
				color: #fff;
			}
			.check_more{
				padding: 4rpx 8rpx;
				background-color: #000;
				color: #fff;
				border-radius: 5px;
			}
		}
		.detail_scan_warp{
			width: 90%;
			padding: 25rpx 10rpx;
			text-align: center;
			box-shadow: 0px 5px  10px 5px #ebebeb;
			.count_wrap{
				// display: flex;
				// flex-direction: column;
				font-size: 25rpx;
				width: 50%;
				float: left;
			}
			progress{
				width: 50%;
				overflow: hidden;
				border: 1px solid #000;
				margin: 40rpx auto;
				margin-top: 120rpx;
				// border-radius: 10px;
				.uni-progress-bar{
					background-color: #fff !important;
				}
			}
		}
		.detail_scan_bottom{
			width: 87%;
			height: 20rpx;
			background-color: #FE9041;
			overflow: hidden;
			border-radius: 0 0 15px 15px;
		}
		.mid_bar{
			margin-top: 25rpx;
			display: flex;
			.borrow_book_wrap{
				flex: 1;
				margin: 10rpx;
				width: 280rpx;
				height: 170rpx;
				/* #ifdef MP-WEIXIN */
				width: 300rpx;
				height: 200rpx;
				/* #endif */
				// background-color: #A3E3FC;
				border-radius: 10rpx;
				border: 2px solid #9FF6CD;
				padding: 20rpx;
				text{
					font-size: 40rpx;
					font-weight: 600;
					line-height: 170rpx;
					/* #ifdef MP-WEIXIN */
					line-height: 150rpx;
					/* #endif */
					color: #38761D;
				}
				view{
					float: right;
					line-height: 170rpx;
					/* #ifdef MP-WEIXIN */
					line-height: 150rpx;
					/* #endif */
                    color: #38761D;
					font-size: 40px;
				}
			}
			.borrow_book_wrap:nth-child(2){
				border: 2px solid #A3E3FC;
				text{
					color: #45818E;
				}
				view{
					color: #45818E;
				}
			}
		}
		.hot_title_wrap{
			margin-top: 20rpx;
			width: 90%;
			// border-bottom: 1px solid #4a4a4a;
			.hot_title{
				width: 125rpx;
				/* #ifdef MP-WEIXIN */
				  width: 170rpx;
				/* #endif */
				border-radius: 10rpx 0 10rpx 0;
				padding: 5rpx 20rpx;
				// border: 1px solid #000;
				border-bottom: none;
				background-color: #FF6B00;
				color: #fff;
			}
		}
		.hot_wrap{
			width: 90%;
			box-shadow: 0 10px  10px 5px #ebebeb;
			margin-bottom: 150rpx;
			.img{
			    height: 235rpx !important;
			}
			.hot_tag_wrap{
			    view{
			    	display: inline-block;
			    	font-size: 25rpx;
			    	color: #fff;
			    	padding: 5rpx 15rpx;
			    	border-radius: 15rpx;
			    	background: linear-gradient(130deg,red,orange);
			    	margin-top: 20rpx;
			    	text{
			    		color: #565656;
			    		font-size: 20rpx;
			    		margin-left: 10rpx;
			    	}
			    }
			}
			.hot_item_wrap:nth-child(2){
				.hot_tag_wrap{
					view{
						background: linear-gradient(130deg,orange,#ff7e15);
					}
				}
			}
			.hot_item_wrap:nth-child(3){
				.hot_tag_wrap{
					view{
						background: linear-gradient(130deg,orange,yellow);
					}
				}
			}
			.hot_item_wrap:last-child{
				.hot_item{
					border-bottom: none;
				}
				
			}
		}
	}
</style>
