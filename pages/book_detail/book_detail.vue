<template>
	<view class="book_detail">
		<swiper @change="onChange" :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000" circular="true" indicator-active-color="#fff">
			<swiper-item @click="previewImage" v-for=" (item,index) in swiperList" :key="index">
				<image src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fp1.itc.cn%2Fq_70%2Fimages03%2F20220422%2F4452d58683154e3598632ac152530961.jpeg&refer=http%3A%2F%2Fp1.itc.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1654742688&t=1f88524268f90a6d2747475e7882ca81" mode=""></image>
			</swiper-item>
		</swiper>
		<view class="book_top">
			<view class="book_name">
				<text>《哈利波特与死亡圣器》</text>
				<text>￥100</text>
			</view>
			<view class="book_condition">
				<view class="tag">
					<u-tag v-for="(item,index) in tagList" :key="index" :text="item" size="mini" class="tag_item" type="warning" plain plainFill></u-tag>
				</view>
				<u-toast ref="uToast2"></u-toast>
				<view class="button">
					<view @click="addBookShelf">加入书架</view>
					<view @click="borrowNow">立即借阅</view>
				</view>
			</view>
		</view>
		<view class="book_detail_introduction">
			<view class="title">
				内容简介
			</view>
			<u-read-more class="info" :toggle="true" :showHeight='150' :fontSize='28' color='#ff9a41'>
			    <rich-text :nodes="content"></rich-text>
			</u-read-more>
			<!-- <view class="info">
				《哈利·波特与死亡圣器》（Harry Potter and the Deathly Hallows）是英国女作家J·K·罗琳创作的长篇小说，是魔幻小说《哈利·波特》系列的第七本，也是系列的最后一本。
				《圣器》主要讲述了十七岁的哈利本应在霍格沃茨魔法学校继续最后一年的学业，但为了完成己故魔法学校前任校长邓布利多留给他消灭伏地魔的任务，哈利和好友面对伏地魔及其追随者食死徒的围追堵截，隐形循迹、历经艰险，最终销毁多个魂器并战胜伏地魔，取得魔法世界伟大胜利的故事。
			</view> -->
		</view>
		<view class="evaluate">
			<view class="title">
				<text>内容评价</text>
				<text @click="checkMore">查看更多
				    <uni-icons type="right" color="#000000" size="15" />
				    <!-- #ifdef MP-WEIXIN -->
				    <text class="iconfont icon-youyou-"></text>
				    <!-- #endif -->
				</text>
			</view>
			<view class="evaluate_wrap">
				<view class="evaluate_item">
					<view class="evaluate_top">
						<image src="https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500" mode=""></image>
						<view class="name_wrap">
							<text>t****1</text>
							<text>13天前</text>
						</view>
					</view>
					<view class="content">
					     书非常好看，一周看完了，回味无穷！！
				    </view>
				</view>
				<view class="evaluate_item">
					<view class="evaluate_top">
						<image src="https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500" mode=""></image>
						<view class="name_wrap">
							<text>t****1</text>
							<text>13天前</text>
						</view>
					</view>
					<view class="content">
					     书非常好看，一周看完了，回味无穷！！
				    </view>
				</view>
			</view>
		</view>
		<view class="recommend_wrap">
			<view class="title">
				相关推荐
			</view>
			<view class="recommend_book_wrap">
				<view class="recommend_book_item">
					<image src="https://img1.baidu.com/it/u=1275895507,934482785&fm=253&fmt=auto&app=120&f=JPEG?w=459&h=650" mode=""></image>
					<view class="name">
					   《活着》
					</view>
				</view>
			</view>
		</view>
		<u-popup :show="isShow" mode="bottom" :closeable="true"  @close="close" @open="open">
		     <view class="borrow_wrap">
		     	<view class="book_info_wrap">
		     		<image src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimage.96192.com%2Fproduct_pic%2Fimagewx%2F18012872%2F1200982088_32_1.jpg&refer=http%3A%2F%2Fimage.96192.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1655952676&t=1ff422bd11f76685e5d932b9d304a951" mode=""></image>
					<view class="info_wrap">
						<view class="name">
							《哈利波特与死亡圣器》
						</view>
						<view class="price">
							押金<text>￥100</text>
						</view>
						<view class="tag">
							<u-tag v-for="(item,index) in tagList" :key="index" :text="item" size="mini" class="tag_item" type="warning" plain plainFill></u-tag>
						</view>
					</view>
		     	</view>
				<view class="book_position_wrap">
					<view class="title">
						位置<text>2楼A区1号书架第5层</text>
					</view>
				</view>
				<view class="book_position_wrap">
					<view class="title">
						书籍选择
					</view>
					<view class="option_wrap">
						<u-toast ref="uToast"></u-toast>
						<view class="option_item" @click="selectBook(index,item)" :class="{'no': item===0 ,'active': index===currentBook}"  v-for=" (item,index) in bookList" :key="index">
							5-{{index+1}}
						</view>
					</view>
				</view>
				<view class="book_position_wrap subscribe_wrap">
					<view class="title">
						预约期限
					</view>
					<view class="example-body">
						<uni-datetime-picker type="daterange" @change="maskChange" />
					</view>
				</view>
				<view class="comfirm">
					<button :class="currentBook >= 0?'active':''" @click="comfirmBorrow">确认</button>
				</view>
		     </view>
		</u-popup>
		<view >
		     <u-modal @confirm="clickTipYes" :show="tipShow" :title="title" :content='tipContent'></u-modal>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				dateSelect:false,
				cell:{
					message:'已被借走',
					duration:800
				},
				cell0:{
					message:'请选择日期',
					duration:800
				},
				cell2:{
					message:'加入书架成功',
					duration:800
				},
				tipShow:false,
				isShow:false,
				currentBook:-1,
				swiperList:[1,2,3,4],
				bookList:[1,1,0,1,0,1],
				title:'借阅成功',
				tipContent:'请自行前往图书所在位置取书.',
				tagList:['少儿','魔法','冒险'],
				currentIndex:0,
				content:`《哈利·波特与死亡圣器》（Harry Potter and the Deathly Hallows）是英国女作家J·K·罗琳创作的长篇小说，是魔幻小说《哈利·波特》系列的第七本，也是系列的最后一本。
				         《圣器》主要讲述了十七岁的哈利本应在霍格沃茨魔法学校继续最后一年的学业.
						 但为了完成己故魔法学校前任校长邓布利多留给他消灭伏地魔的任务，哈利和好友面对伏地魔及其追随者食死徒的围追堵截，隐形循迹、历经艰险，最终销毁多个魂器并战胜伏地魔，取得魔法世界伟大胜利的故事。`
			}
		},
		methods: {
			previewImage(){
				uni.previewImage({
					urls:['https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fp1.itc.cn%2Fq_70%2Fimages03%2F20220422%2F4452d58683154e3598632ac152530961.jpeg&refer=http%3A%2F%2Fp1.itc.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1654742688&t=1f88524268f90a6d2747475e7882ca81',
					'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fp1.itc.cn%2Fq_70%2Fimages03%2F20220422%2F4452d58683154e3598632ac152530961.jpeg&refer=http%3A%2F%2Fp1.itc.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1654742688&t=1f88524268f90a6d2747475e7882ca81',
					'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fp1.itc.cn%2Fq_70%2Fimages03%2F20220422%2F4452d58683154e3598632ac152530961.jpeg&refer=http%3A%2F%2Fp1.itc.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1654742688&t=1f88524268f90a6d2747475e7882ca81',
					'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fp1.itc.cn%2Fq_70%2Fimages03%2F20220422%2F4452d58683154e3598632ac152530961.jpeg&refer=http%3A%2F%2Fp1.itc.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1654742688&t=1f88524268f90a6d2747475e7882ca81',],
					current:this.currentIndex,
					
				})
			},
			onChange(e){
				let index = e.target.current || e.detail.current;
				this.currentIndex=index;
				console.log(index);
			},
			borrowNow(){
				this.isShow=true
			},
			close(){
				this.isShow=false
			},
			maskChange(e){
				this.dateSelect= !this.dateSelect
				console.log(e);
			},
			clickTipYes(){
				this.tipShow=false;
			},
			comfirmBorrow(){
				if(this.currentBook >= 0){
					if(this.dateSelect){
						this.tipShow=true;
					}
					else{
						const params = this.cell0
						this.$refs.uToast.show({
							...params
						})
					}
				}
				
			},
			selectBook(i,item){
				if(item!=0){
					this.currentBook=i;
				}else{
					this.currentBook= -1;
					const params = this.cell;
					this.$refs.uToast.show({
						...params
					})
				}
			},
			checkMore(){
				uni.navigateTo({
					url:'../checkMoreComments/checkMoreComments'
				})
			},
			addBookShelf(){
				const params = this.cell2;
				this.$refs.uToast2.show({
					...params
				})
			}
		}
	}
</script>

<style lang="scss">
.book_detail{
	background-color: #f5f5f5;
	swiper{
		width: 100%;
		height: 380rpx;
		image{
			width: 100%;
			// height: 500rpx;
		}
	}
	.book_top{
		background-color: #fff;
		padding-top: 25rpx;
		margin: 0 10rpx;
		position: relative;
		top: -40rpx;
		border-radius: 15rpx 15rpx 0 0 ;
		height: 200rpx;
		.book_name{
			display: flex;
			justify-content: space-between;
			font-weight: 600;
			margin: 0 20rpx;
			text:last-child{
				color: red;
			}
		}
		.book_condition{
			display: flex;
			margin-top: 50rpx;
			.tag{
				flex: 1;
				display: flex;
				// justify-content: center;
				margin-left: 20rpx;
				// margin-top: 20rpx;
				.tag_item{
					margin: 0 8rpx;
				}
			}
			.button{
				flex: 1;
				display: flex;
				view{
					font-size: 25rpx;
					box-shadow: 0 0 10rpx 1rpx #aaaaaa;
					padding: 10rpx 25rpx;
					margin: 0 10rpx;
					border-radius: 15rpx;
				}
			}
		}
	}
	.book_detail_introduction{
		background-color: #fff;
		margin: 0 15rpx;
		border-radius: 15rpx;
		padding: 10rpx;
		.title{
			font-weight: 700;
		}
		.info{
			// height: 500rpx;
			rich-text{
				height: 1000rpx;
			}
		}
	}
	.evaluate{
		background-color: #fff;
		margin: 20rpx 15rpx;
		border-radius: 15rpx;
		padding: 10rpx;
		.title{
			// font-size: 33rpx;
			font-weight: 700;
			display: flex;
			justify-content: space-between;
		}
		.evaluate_wrap{
			margin-top: 20rpx;
			.evaluate_item{
				.evaluate_top{
				    display: flex;
					image{
						margin: 0 15rpx;
						width: 75rpx;
						height: 75rpx;
						border-radius: 50%;
					}
					.name_wrap{
						display: flex;
						flex-direction: column;
						font-size: 28rpx;
						margin-top: 5rpx;
						text:first-child{
							
						}
							
						text:last-child{
							font-size: 25rpx;
							color: gray;
						}
					}
				}
				.content{
					font-size: 30rpx;
					margin: 20rpx;
				}
			}
		}
	}
	.recommend_wrap{
		background-color: #fff;
		margin: 20rpx 15rpx;
		border-radius: 15rpx;
		padding: 10rpx;
		.title{
			font-weight: 700;
		}
		.recommend_book_wrap{
			margin: 20rpx 10rpx;
			.recommend_book_item{
				display: flex;
				flex-direction: column;
				text-align: center;
				width: 180rpx;
				// border: 1rpx solid #c8c8c8;
				border-radius: 15rpx;
				image{
					width: 180rpx;
					height: 230rpx;
					border-radius: 15rpx; 
				}
				view{
					margin: 10rpx 0; 
				}
			}
		}
	}
     .borrow_wrap{
		 .book_info_wrap{
			 display: flex;
			 padding: 20rpx;
			 image{
				 flex: 1;
				 // width: 200rpx;
				 height: 230rpx;
			 }
			 .info_wrap{
				 flex: 3;
				 margin-left: 50rpx;
				.name{
					font-weight: 700;
					margin-top: 40rpx;
					line-height: 50rpx;
				} 
				.price{
					color: gray;
					line-height: 80rpx;
					margin-left: 18rpx;
					text{
						margin-left: 10rpx;
						font-weight: 700;
					    color: red;
					}
				}
				.tag{
					flex: 1;
					display: flex;
					flex-wrap: wrap;
					margin: 10rpx;
					.tag_item{
						margin: 0 8rpx;
					}
				}
			 }
		 }
		 .book_position_wrap{
			 margin: 20rpx;
			 box-shadow: 0 0 10rpx 5rpx #eee;
			 padding: 20rpx;
			 .title{
				 margin: 10rpx 0;
				 font-weight: 700;
				 text{
					 font-weight: normal;
					 font-size: 30rpx;
					 margin-left: 20rpx;
				 }
			 }
			 .example-body{
				 margin: 20rpx 10rpx ;
			 }
			 .option_wrap{
				 display: flex;
				 flex-wrap: wrap;
				 margin: 10rpx 0;
				 .option_item{
					 font-size: 28rpx;
					 margin: 10rpx;
					 padding: 5rpx 25rpx;
					 border: 1px solid #000000;
					 border-radius: 15rpx;
				 }
				 .active{
					color: coral; 
					border-color: coral;
				 }
				 .no{
					 color: gray;
					 border-color: #bebebe;
				 }
			 }
		 }
		 .comfirm{
			 padding: 20rpx 80rpx;
			 button::after{
				 border: none;
			 }
			 button{
				background-color: #fff;
				color: gray;
				 border: 1px solid gray;
			 }
			 .active{
				 background-color: #fff;
				 color: coral;
				 border: 1px solid coral;
			 }
		 }
	 }
}
</style>
