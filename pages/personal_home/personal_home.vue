<template>
	<view class="personal_home">
		<view class="nav_bar_top"></view>
		<uni-nav-bar class="home_navbar" leftWidth="70rpx">
			    <block slot="left">
			    	<view class="city" @click="goBack">
			    		<uni-icons type="back" color="#666" size="25" />
			    	</view>
			    </block>
		    <my-input :text="text"></my-input>
			
		    <block slot="right">
				<view class="city" @click="scan">
					<uni-icons class="input-uni-icon" type="more-filled" size="30" color="#999" />
				</view>
		    </block>
		</uni-nav-bar>
		<view class="personal_wrap">
			<view class="personal_info">
				<image src="https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500" mode=""></image>
				<view class="right">
					<info-bar :infoList="generalInfo"></info-bar>
					<view class="button_wrap">
						<view class="button_item">
							关注
						</view>
						<view class="button_item">
							私信
						</view>
					</view>
				</view>
			</view>
			<view class="personal_detail">
				<view class="name">
					张三
				</view>
				<view class="university">
					认证：西南石油大学
				</view>
			</view>
		</view>
		<view class="content_wrap">
			<view class="select_wrap">
				<view class="option" :class="current===0?'active':'' " @click="change(0)">
					书架
				</view>
				<view class="option" :class="current===1?'active':'' " @click="change(1)">
					动态
				</view>
				
			</view>
			<view class="content" v-show="current===0">
				<book-shelf></book-shelf>
			</view>
			<view class="post_wrap" v-show="current===1">
				<view class="post_item" v-for="(item ,index) in [1]" :key="index">
					<view class="post_main">
						<image src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fup.enterdesk.com%2Fedpic_source%2F33%2F6d%2F82%2F336d82ec4a3fc5cf5add5c347946452e.jpg&refer=http%3A%2F%2Fup.enterdesk.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656480958&t=97a0ebd5057e3b695c131b0aa53efb09" mode=""></image>
						<view class="right">
							<view class="name">
								萧赞
							</view>
							<view class="content">
								小面包又来害我了！
								小面包又来害我了！
								
								小面包又来害我了！
								小面包又来害我了！
								小面包又来害我了！
								小面包又来害我了！
							</view>
							<view class="image_wrap">
								<u-album singleSize="520rpx" multipleSize="150rpx" rowCount="3" :urls="urls2"></u-album>
							</view>
						</view>
					</view>
					<view class="post_bottom">
						<view class="date">
							2022-05-09
						</view>
						<view class="other">
							<uni-icons class="icon" type="heart" color="#595959" size="20" />12
							<uni-icons class="icon" type="chatbubble" color="#595959" size="20" />2
						</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import InfoBar from '../../components/infoBar.vue'
	import BookShelf from '../../components/bookshelf.vue'
	import MyInput from '../../components/input.vue'
	export default {
		components:{
			InfoBar,
			BookShelf,
			MyInput
		},
		data() {
			return {
				 urls2: [
				     'https://cdn.uviewui.com/uview/album/1.jpg',
				     'https://cdn.uviewui.com/uview/album/2.jpg',
				     'https://cdn.uviewui.com/uview/album/3.jpg',
				     // 'https://cdn.uviewui.com/uview/album/4.jpg',
				     // 'https://cdn.uviewui.com/uview/album/5.jpg',
				     // 'https://cdn.uviewui.com/uview/album/6.jpg',
				     // 'https://cdn.uviewui.com/uview/album/7.jpg',
				     // 'https://cdn.uviewui.com/uview/album/8.jpg',
				     // 'https://cdn.uviewui.com/uview/album/9.jpg',
				     // 'https://cdn.uviewui.com/uview/album/10.jpg',
				 ],
				generalInfo:[10,2,12,0],
				current:0,
				text:'输入关键词搜索'
			}
		},
		methods: {
			change(i){
				this.current=i;
			},
			goRecommendDetail(){
				uni.navigateTo({
					url:'../recommend/recommend'
				})
			},
			goBack(){
				uni.navigateBack({
					
				})
			}
		}
	}
</script>

<style lang="scss">
.personal_home{
	background-color: #eee;
	// height: 100vh;
	// overflow: auto;
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
    .personal_wrap{
		margin-top: 170rpx;
		padding: 15rpx 20rpx;
		// border-bottom: 1rpx solid #c1c1c1;
		background-color: #fff;
		.personal_info{
			display: flex;
			image{
				flex: 1;
				height: 190rpx;
				// width: 200rpx;
			}
			.right{
				flex: 2.3;
				display: flex;
				flex-direction: column;
				margin-left: 80rpx;
				.button_wrap{
					display: flex;
					margin: 20rpx 50rpx;
					.button_item{
						flex: 1;
						margin: 0 10rpx;
						padding: 5rpx 0;
						text-align: center;
						background-color: #fff;
						color: #535353;
						border: 1px solid #535353;
					}
				}
			}
		}
		.personal_detail{
			margin-left: 70rpx;
			.university{
				margin-top: 10rpx;
				font-size: 28rpx;
				color: #535353;
			}
		}
	}
	.content_wrap{
		margin: 10rpx 0;
		margin-bottom: 100rpx;
		.select_wrap{
			display: flex;
			justify-content: center;
			background-color: #fff;
			.option{
				text-align: center;
				flex: 1;
				margin: 10rpx 30rpx;
			}
			.active{
				color: coral;
			}
		}
		.content{
			margin-top: 10rpx;
			background-color: #fff;
			border-radius: 15rpx;
		}
	}
	.post_wrap{
		margin: 20rpx 0;
		.post_item{
		   
			// margin-bottom: 20rpx;
		    background-color: #fff;
			border-bottom: 1px solid #d6d6d6;
			.post_main{
				 display: flex;
				 image{
				 	width: 100rpx;
				 	height: 100rpx;
				 	margin: 20rpx;
				 }
				 .right{
				 	display: flex;
				 	flex-direction: column;
				 	.name{
				 		font-weight: 600;
				 		font-size: 38rpx;
				 		margin-top: 20rpx;
				 		// line-height: 90px;
				 	}
				 	.content{
				 		width: 580rpx;
				 		color: #6d6d6d;
				 	}
				 	.image_wrap{
				 		width: 580rpx;
				 		margin: 20rpx 0;
						.u-album__row{
							.u-album__row__wrapper{
								margin-right: 0rpx !important;
							}
						}
						
				 	}
				 }
			}
			.post_bottom{
				display: flex;
				justify-content: space-between;
				padding-left: 140rpx;
				padding-right: 100rpx;
				margin-bottom: 20rpx;
				color: #666;
				.date{
					font-size: 25rpx;
				}
				.other{
					.icon{
						margin: 0 15rpx;
					}
				}
			}
		}
	}
}
</style>
