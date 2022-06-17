<template>
	<view class="personal">
		<view class="nav_bar_top"></view>
		<uni-nav-bar class="personal_navbar" leftWidth="80rpx">
			<!-- #ifdef MP-WEIXIN -->
			   <block slot="left">
			   	   <view class="city" @click="goNews">
					   <view class="point"></view>
			   	   	   <uni-icons class="input-uni-icon" type="chat" size="25" color="#999" />
			   	   </view>
			   </block>
			   <!-- #endif -->
			<!-- #ifdef APP-PLUS || H5-->
			<block slot="right">
				<view class="city" @click="goNews">
					<view class="point"></view>
					<uni-icons class="input-uni-icon" type="chat" size="28" color="#999" />
				</view>
			</block>
			<!-- #endif -->
		</uni-nav-bar>
		<view class="headImage">
			<view class="image_wrap" @click="goPersonalHome">
			     <!-- #ifdef MP-WEIXIN -->
			       <image src="https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500" mode=""></image>
			      <!-- #endif -->
			      <!-- #ifndef MP-WEIXIN -->
			     <image :style="myStyle" src="https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500" mode=""></image>
			      <!-- #endif -->
			 </view>
			<view class="content">
				<text class="name">张三</text>
				<text>院校：西南石油石油石油大学</text>
			</view>
			<view class="vip" @click="goMember">
				会员中心<uni-icons type="right" color="#ff924a" size="15" />
			</view>
		</view>
		<info-bar :infoList="generalInfo"></info-bar>
		<view class="info_bar" style="margin: 0 20rpx; margin-top: 50rpx; color: #000; 
		                        box-shadow: 0 0  10px 2px #ebebeb;">
								
			<view class="info_bar_item" @click="goBookshelf">
				<text class="iconfont icon-shujia"></text>
				<text>书架</text>
			</view>
			<view class="info_bar_item" @click="goSubscription">
				<text class="iconfont icon-dingyue" ></text>
				<text>我的订阅</text>
			</view>
			<view class="info_bar_item" @click="goRecord">
					<text class="iconfont icon-yyjl"></text>
				<text>我的记录</text>
			</view>
			<view class="info_bar_item" @click="goHistory">
				<text class="iconfont icon-cebianlan-lishiliulan-weixuanzhong"></text>
				<text>历史浏览</text>
			</view>
		</view>
		<view class="offen_scan">
			<view class="offen_scan_top">
				<text class="my_scan">我的经常浏览</text>
				<text @click="goAlwaysScan">
					查看更多
				     <uni-icons type="right" color="#818181" size="15" />
				        <!-- #ifdef MP-WEIXIN -->                             <text class="iconfont icon-youyou-"></text>
					    <!-- #endif -->
				</text>
			</view>
			<scroll-view scroll-x="true" class="scan_content">
				<view class="scan_content_item" v-for="(item,index) in list" :key="index">
					<image src="https://img1.baidu.com/it/u=1275895507,934482785&fm=253&fmt=auto&app=120&f=JPEG?w=459&h=650" mode=""></image>
					<text>活着</text>
				</view>
			</scroll-view>
		</view>
		<view class="more_wrap">
			<view class="more_top">更多服务</view>
			<view class="more_content">
				<view class="more_content_item" v-for="(item,index) in moreList" :key="index" @click="goto(index)">
				    <view class="">
						<text class="u_icon iconfont" :class="item.icon"></text>
						<!-- <uni-icons class="u_icon" :type="item.icon" color="#ffbd72" size="20" /> -->
				    	<text>{{item.name}}</text>
				    </view>	
					<view class="">
						<uni-icons type="right" color="#000000" size="18" />
					</view>
				</view>
			</view>
		</view>
		.
		<!-- #ifdef MP-WEIXIN -->
		   <TabBar :current-page="4" />
		<!-- #endif -->
	</view>
</template>

<script>
	import InfoBar from '../../components/infoBar.vue'
	export default {
		components:{
			InfoBar
		},
		data() {
			return {
				generalInfo:[10,2,12,0],
				list:[1,1,1,1,1,1,1,1,1,1,1],
				moreList:[{
					icon:'icon-shezhi',
					name:'设置'
				},{
					icon:'icon-gerenxinxi',
					name:'个人信息'
				},{
					icon:'icon-yuqi',
					name:'逾期记录'
				},{
					icon:'icon-kefu',
					name:'联系客服'
				},{
					icon:'icon-yijianfankui',
					name:'意见反馈'
				},{
					icon:'icon-yinsibaohu',
					name:'隐私政策'
				}],
				myStyle: {
					width: 135 + 'rpx',
					height: 135 + 'rpx'
				}
			}
		},
		methods: {
			login(){
				// #ifndef MP-WEIXIN
				   // uni.navigateTo({
				   // 	url:'../login/login'
				   // })
				   uni.login({
					   // provider: 'univerify',
				   	  univerifyStyle: { 
				   	      fullScreen: true
				   	    },
						success:function(res){
							console.log(res);
						}
				   })
				// #endif
				// #ifndef MP-WEIXIN
				uni.login({
					onlyAuthorize
				})
				// #endif
			},
			goMember(){
			   uni.navigateTo({
			   	url:'../member/member'
			   })
		    },
			goBookshelf(){
				uni.navigateTo({
					url:'../bookshelf/bookshelf'
				})
			},
			goSubscription(){
				uni.navigateTo({
					url:'../subscription/subscription'
				})
			},
			goRecord(){
				uni.navigateTo({
					url:'../record/record'
				})
			},
			goHistory(){
				uni.navigateTo({
					url:'../history/history'
				})
			},
			goPersonalHome(){
				uni.navigateTo({
					url:'../personal_home/personal_home'
				})
			},
			goNews(){
				uni.navigateTo({
					url:'../news/news'
				})
			},
			goAlwaysScan(){
				uni.navigateTo({
					url:'../always_scan/always_scan'
				})
			},
			goto(i){
				if(i==2){
					uni.navigateTo({
						url:'../overdue/overdue'
					})
				}
			}
		},
		onPageScroll(e){
			// console.log(e.scrollTop);
			// #ifndef MP-WEIXIN
			if(e.scrollTop < 60 && e.scrollTop >30){
			     this.myStyle.width= 145-e.scrollTop + 'rpx'
			     this.myStyle.height= 145-e.scrollTop + 'rpx'
				
			}
			else if(e.scrollTop > 60 ){
			     this.myStyle.width= 80 + 'rpx'
			     this.myStyle.height= 80 + 'rpx'
			}
			 if (e.scrollTop < 30){
				this.myStyle.width= 135+ 'rpx'
				this.myStyle.height= 135+ 'rpx'
			}
			// #endif
		},
		
	}
</script>

<style lang="scss">
.personal{
	background-color: #fafafa;
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
	.personal_navbar{
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
			position: relative;
			.point{
				position: absolute;
				top: 4rpx;
				right: 4rpx;
				width: 10rpx;
				height: 10rpx;
				border-radius: 50%;
				background-color: red;
			}
		}
	}
    .headImage{
		background-color: #fff;
		margin: 0 5rpx;
		margin-top: 165rpx;
		display: flex;
		width: 100%;
		.image_wrap{
			// 吸顶父元素
			// background-color: #ff924a;
			/* #ifndef MP-WEIXIN*/
			position: absolute;
			top: 170rpx;
			width: 1rpx;
			height: 1305rpx;
			/* #endif */
			/* #ifdef H5 */
			 top: 20rpx;
			/* #endif */
			
			margin-left: 20rpx;
			/* #ifdef MP-WEIXIN*/
			    margin-left: 10rpx;
			/* #endif */
			image{
		    	/* #ifndef MP-WEIXIN*/
		    	    position: sticky;
					top: 50rpx;
		    	    z-index: 11;
		    	/* #endif */
		    	width: 135rpx;
		    	height: 135rpx;
		    }
		}
		
		.content{
			margin: 30rpx;
			/* #ifndef MP-WEIXIN*/
			margin-left: 180rpx;
			/* #endif */
			display: flex;
			flex-direction: column;
			justify-content: end;
			width: 340rpx;
			text{
				overflow: hidden;    
			    text-overflow: ellipsis;    
			    white-space: nowrap;
			}
			.name{
				font-size: 40rpx;
				font-weight: 700;
			}
		}
		.vip{
			color: #ff924a;
			line-height: 170rpx;
			font-weight: 700;
			margin-right: 20rpx;
		}
	}
	.info_bar{
		background-color: #fff;
		color: gray;
		display: flex;
		// width: 100%;
		border-radius: 10rpx;
		padding: 10rpx 0;
		text-align: center;
		padding-top: 30rpx;
		// margin-top: 30rpx;
		.info_bar_item{
			flex: 1;
			display: flex;
			flex-direction: column;
			margin: 0 10rpx;
			// border-right: 1rpx solid #eee;
			text{
				align-items: center;
				margin-top: 5rpx;
				font-size: 25rpx
			}
			.iconfont{
				color: #ff924a;
				font-size: 55rpx;
			}
		}
		.info_bar_item:last-child{
			border-right: none;
		}
	}
	.offen_scan{
		margin: 40rpx auto;
		// display: flex;
		width: 95%;
		border-radius: 10rpx;
		padding: 10rpx;
		// border: 1px solid #ebebeb;
		background-color: #fff;
		// box-shadow: 0 0  10px 2px #ebebeb;
		.offen_scan_top{
			display: flex;
			justify-content: space-between;
			padding: 0 25rpx;
			margin-bottom: 25rpx;
			color: gray;
			.my_scan{
				color: #000;
			}
		}
		.scan_content{
			// display: flex;
			margin-top: 10rpx;
			width: 100%;
			// height: 255rpx;
			overflow: hidden;
			white-space: nowrap;
			.scan_content_item{
				display: inline-block;
				width: 180rpx;
				height: 230rpx;
				text-align: center;
				// background-color: #ffbc6e;
				// display: flex;
				// flex-direction: column;
				// text-align: center;
				margin: 0 5rpx;
				image{
					position: sticky;
					width: 150rpx;
					height: 170rpx;
				}
				text{
					font-size: 25rpx;
					display: block;
					margin: 2rpx 30rpx;
					overflow: hidden;
					text-overflow: ellipsis;    
					white-space: nowrap;
				}
			}
		}
	}
    .more_wrap{
		margin-bottom: 340rpx;
		/* #ifdef APP-PLUS */
			margin-bottom: 350rpx;
		/* #endif */
		.more_top{
			font-weight: 700;
			margin-left: 25rpx;
		}
		.more_content{
			
			background-color: #fff;
			width: 92%;
			margin: 15rpx auto;
			padding: 5rpx 15rpx;
			box-shadow:  0 0 5rpx 2rpx #ebebeb;
			.more_content_item{
				display: flex;
				justify-content: space-between;
				padding: 20rpx 0;
				border-bottom: 1px solid #ebebeb;
				.u_icon{
					// color: #ff9252;
					margin: 0 15rpx;
				}
				text{
				}
			}
			.more_content_item:last-child{
				border-bottom: none;
			}
		}
	}
}
</style>
