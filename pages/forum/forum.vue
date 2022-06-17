<template>
	<view class="fotum">
			<view class="nav_bar_top"></view>
			<!-- #ifdef MP-WEIXIN -->
			<uni-nav-bar class="fotum_navbar" leftWidth="180rpx" rightWidth="50rpx">
				<block slot="left">
				   <view class="city" @click="backTo">
				   	   	<uni-icons class="input-uni-icon" type="plusempty" size="25" color="#2a8aff" @click="goWrite" />
				   </view>
				</block>
				
			    <view class="input-view">
					  <u-tabs :activeStyle="{
                                   color: '#303133',
                                   fontWeight: 'bold',
                                   transform: 'scale(1.05)'
                                   }" :list="tabBars" @click="click" :current="tabIndex"></u-tabs>
			   </view>
			</uni-nav-bar>
			<!-- #endif -->
			<!-- #ifdef APP-PLUS || H5-->
			<uni-nav-bar class="fotum_navbar" leftWidth="26%" rightWidth="50rpx">
				<view class="input-view">
					  <u-tabs :activeStyle="{
                                   color: '#303133',
                                   fontWeight: 'bold',
                                   transform: 'scale(1.05)'
                                   }" lineWidth="30rpx" :list="tabBars" @click="click" :current="tabIndex" ></u-tabs>
				</view>
				<block slot="right">
					<view class="city" @click="cancel">
						 <uni-icons class="input-uni-icon" type="plusempty" size="25" color="#ff973c" @click="goWrite"/>
					</view>
				</block>
			</uni-nav-bar>
			<!-- #endif -->
			<view class="line-h"></view>
			<swiper :current="tabIndex" class="swiper-box" style="flex: 1;" :duration="300" @change="ontabchange">
			    <!-- 想法 -->
				<swiper-item class="swiper-item" >
					<scroll-view class="scroll-v" enableBackToTop="true" scroll-y @scrolltolower="loadMore(1)">
						<view class="idea_wrap">
							<view class="idea_item" @click="goIdea" v-for="(item,index) in list" :key="index">
								<image src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.jj20.com%2Fup%2Fallimg%2Ftp01%2F1ZZQ20QJS6-0-lp.jpg&refer=http%3A%2F%2Fimg.jj20.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1655349536&t=176f040906c0fff7240efc5294ecfef9" mode=""></image>
								<view class="name">
									<view class="left">
										<image src="https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500" mode=""></image>
										<text>water</text>
									</view>
									<view class="right">
						                 <uni-icons class="input-uni-icon" type="heart-filled" size="20" color="#ff0000" />
										 <text>1</text>
									</view>
								</view>
							</view>
							<view class="idea_item" v-for="(item,index) in list" :key="index">
								<image src="https://img0.baidu.com/it/u=3862781436,3930243715&fm=253&fmt=auto&app=138&f=JPEG?w=690&h=460" mode=""></image>
								<view class="name">
									<view class="left">
										<image src="https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500" mode=""></image>
										<text>water</text>
									</view>
									<view class="right">
							             <uni-icons class="input-uni-icon" type="heart-filled" size="20" color="#ff0000" />
										 <text>1</text>
									</view>
								</view>
							</view>
						</view>
					</scroll-view>
			    </swiper-item>
				<!-- 推荐 -->
				<swiper-item class="swiper-item" >
					<scroll-view class="scroll-v" enableBackToTop="true" scroll-y @scrolltolower="loadMore(1)">
						<view class="input-view">
							<input confirm-type="search" class="nav-bar-input" type="text" placeholder="输入搜索关键词" v-model="searchInfo" :focus="isFoucus"
								@confirm="confirm" />
							<uni-icons class="input-uni-icon" type="search" size="18" color="#999" />
						</view>
						<view class="recommend_content" @click="goRecommendDetail" v-for="(item,index) in list" :key="index">
							<view class="content_title">
								前端零基础自学：相互监督学习，一起自学找工作！
							</view>
							<view class="name">
								<image src="https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500" mode=""></image>
								<text>西瓜少年</text>
							</view>
							<view class="content">
								本书前一部分写了在毛泽东以前的中共领袖史，描述了历史对他们的走马灯般的淘汰。如列宁所说︰“他们当领袖是不合格的，看来他们在革命期间将不得不由领袖变为下屈，否则就会被抛弃。”中间一部分描写秋收起义失败后毛泽东在井冈山建立革命根据地后展现出的军事才能，这其中从以第一次反围剿到第五次反围剿无一不展示出毛泽东卓越的军事政治才能。到了最后部分重点描述从遵义会议确立毛泽东的领袖地位之后，面临张国焘和王明两次严重的挑战，直至中共“七大”把毛泽东思想作为指导方针写入中共党章。
							</view>
							<view class="content_bottom">
								<text>177赞同</text>
								<text>448收藏</text>
							</view>
						</view>
					</scroll-view>
				</swiper-item>
				<swiper-item class="swiper-item" >
					<scroll-view class="scroll-v" enableBackToTop="true" scroll-y @scrolltolower="loadMore(1)">
						<view class="hot_wrap">
							<view class="hot_item" v-for="(item,index) in list" :key="index">
								<view class="hot_no">
									{{index+1}}
								</view>
								<view class="hot_content">
									<text>今天逛闲鱼的时候观察到每一行的高度不是相同的,经了解才知道原来这是一种瀑布流布局,感觉挺有意思,于是决定研究一下,在网上也找了一些方案,实现瀑布流大概有3种方式。 一</text>
								    <text>524万浏览</text>
								</view>
								<image src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fccm.ddcdn.com%2Fext%2Fphoto-l%2F17%2Fbb%2F03%2F04%2F1150100-largejpg.jpg&refer=http%3A%2F%2Fccm.ddcdn.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1655366342&t=451071a991c983229568f92ba9e71b80" mode=""></image>
							</view>
						</view>
					</scroll-view>
				</swiper-item>
			</swiper>
         <view class="top_bar">
         </view>
		<!-- #ifdef MP-WEIXIN -->
		   <TabBar :current-page="3" />
		<!-- #endif -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				tabIndex: 1,
				list:[1,1,1,1,,1,1,1,1,1,1,1,1,1,1],
				tabBars: [{
				    name: '想法',
				    id: 'xiangfa'
				}, {
				    name: '推荐',
				    id: 'tuijian'
				}, {
				    name: '热榜',
				    id: 'rebang'
				}, ],
				scrollInto: "",
				showTips: false,
				navigateFlag: false,
				pulling: false,
			}
		},
		methods: {
            click(item) {
				this.tabIndex=item.index;
            },
			ontabchange(e) {
			    let index = e.target.current || e.detail.current;
			    this.tabIndex=index;
				// window.scrollTo(0);
			},
			loadMore(i){
				console.log(i);
			},
			goRecommendDetail(){
				uni.navigateTo({
					url:'../recommend/recommend'
				})
			},
			goIdea(){
				uni.navigateTo({
					url:'../idea/idea'
				})
			},
			goWrite(){
				uni.navigateTo({
					url:'../write/write'
				})
			}
		}
	}
</script>


<style lang="scss">
.fotum{
	display: flex;
	background-color: #f8f8f8;
	.nav_bar_top{
		z-index: 10;
		width: 100%;
		height: 80rpx;
		/* #ifdef MP-WEIXIN */
		   height: 100rpx;
		/* #endif */
		background-color: #fff;
		position: fixed;
		top: 0;
	}
	.fotum_navbar{
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
			margin-left: 0rpx;
			/* #ifdef MP-WEIXIN */
				margin-left: 0rpx;
			/* #endif */
			flex: 1;
			.input-uni-icon{
				margin-left: 10rpx;
			}
		}
	}
    
	/* #ifndef APP-PLUS */
    page {
        width: 100%;
        min-height: 100%;
        display: flex;
    }
    
    /* #endif */
    

    
    .swiper-box {
		margin: 0 15rpx;
		margin-top: 155rpx;
		/* #ifdef MP-WEIXIN */
		   margin-top: 185rpx;
		/* #endif */
		height: 100vh;
		// height: 10000rpx;
        // flex: 1;
    }
    
    .swiper-item {
        // flex: 1;
        // flex-direction: row;
    }
    
    .scroll-v {
        flex: 1;
        /* #ifndef MP-ALIPAY */
        flex-direction: column;
        /* #endif */
        width: 750rpx;
    	width:100%;
		height: 100vh;
		.input-view{
			width: 90%;
			background-color: #ffffff;
			height: 35px;
			border-radius: 15px;
			padding: 0px 15px;
			margin: 7px auto;
			line-height: 30px;
			display: flex;
			flex-direction: row;
			align-items: center;
			flex-wrap: nowrap;
			box-shadow: 0 0 5rpx 1rpx #eee;
			.input-uni-icon{
				margin-left: 20rpx;
			}
			.nav-bar-input{
				width: 100%;
				background-color: #ffffff;
				font-size: 25rpx;
			}
		}
		.recommend_content{
			width: 100%;
			color: gray;
			margin-top: 20rpx;
			background-color: #fff;
			padding: 25rpx 15rpx;
			font-size: 25rpx;
			.content_title{
				color: #000;
				font-size: 30rpx;
				font-weight: 700;
				
			}
			.name{
				margin: 20rpx 5rpx;
				display: flex;
				image{
					width: 60rpx;
					height: 60rpx;
				}
				text{
					margin-left: 15rpx;
					line-height: 55rpx;
				}
			}
			.content{
				display: -webkit-box;
				overflow: hidden;
				text-overflow: ellipsis;
				-webkit-line-clamp: 2;
				-webkit-box-orient: vertical;
				margin-right: 25rpx;
			}
			.content_bottom{
				margin-top: 20rpx;
				text{
					margin-right: 20rpx;
				}
			}
		}
        .idea_wrap{
			width: 100%;
			// column-count: 2;
			// column-gap: 10rpx;
			 display: flex;  
			 // flex-flow: column;
			 flex-wrap: wrap;
			 // flex-flow:column wrap;
			 // height: 100vh;
			 padding-left: 15rpx;
			.idea_item{
				width: 45%;
				margin: 15rpx 15rpx;
				border-radius: 15rpx;
				background-color: #fff;
				text-align: center;
				image{
					width: 300rpx;
					margin: 10rpx auto;
				    border-radius: 5rpx;
				}
				.name{
					color: gray;
					display: flex;
					justify-content: space-between;
					margin-bottom: 5rpx;
					.left{
						display: flex;
						margin-left: 15rpx;
						image{
							width: 55rpx;
							height: 55rpx;
						}
						text{
							margin-left: 10rpx;
							line-height: 65rpx;
						}
					}
					.right{
						margin: 15rpx;
						text{
							margin-left: 5rpx;
						}
				    }
				}
				
			}
		}
		.hot_wrap{
			.hot_item{
				margin: 10rpx;
				padding: 10rpx 20rpx;
				display: flex;
				background-color: #fff;
				border-radius: 15rpx;
				.hot_no{
					margin-left: 15rpx;
					color: red;
					line-height: 140rpx;
					flex: 1;
				}
				.hot_content{
					margin: 10rpx;
				    flex: 9;
					display: flex;
					flex-direction: column;
					justify-content: center;
					text:first-child{
						display: -webkit-box;
				        overflow: hidden;
				        text-overflow: ellipsis;
				        -webkit-line-clamp: 2;
				        -webkit-box-orient: vertical;
					}
					text:last-child{
						color: gray;
						font-size: 25rpx;
						margin-top: 10rpx;
					}
				}
				image{
					margin-top: 30rpx;
					flex: 2;
					// width: 100rpx;
					height: 100rpx;
				}
			}
		}
	}
}
</style>