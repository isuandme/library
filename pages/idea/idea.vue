<template>
	<view class="idea">
		<view class="nav_bar_top"></view>
		<uni-nav-bar class="idea_navbar" leftWidth="60rpx" rightWidth="200rpx">
			<block slot="left">
				<view class="city" @click="backTo">
					<uni-icons type="back" color="#666" size="18" />
				</view>
			</block>
		    <view class="blogger_view">
				<image src="https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500" mode=""></image>
				<view class="name">
					王田田龟女王田田龟女
				</view>
		    </view>
			
			<!-- #ifndef MP-WEIXIN -->
		    <block slot="right">
				<view class="city add" @click="scan">
					+关注
				</view>
				<view class="city" @click="scan">
					<uni-icons class="input-uni-icon" type="more-filled" size="30" color="#999" />
				</view>
		    </block>
			<!-- #endif -->
		</uni-nav-bar>
		<swiper @change="onChange" :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
			<swiper-item @click="previewImage()" v-for="(item,index) in swiperList" :key="index">
				<image src="https://img0.baidu.com/it/u=3862781436,3930243715&fm=253&fmt=auto&app=138&f=JPEG?w=690&h=460" mode=""></image>
			</swiper-item>
		</swiper>
		<view class="idea_content">
			这里的瀑布超好看的！
		</view>
		<view class="issue_time">
			发布于 05-20
		</view>
		<answer-section :answerList="answerList"></answer-section>
		<view class="idea_bottom">
			已经到底了~
		</view>
		<view class="bottom_bar">
			<input type="text" placeholder="说点什么吧~">
			<view class="icon_wrap">
				<view class="icon_item">
					<uni-icons class="icon" type="heart" color="#595959" size="20" />
					<view class="amount">
						12
					</view>
				</view>
				<!-- <view class="icon_item">
					<uni-icons class="icon" type="star" color="#595959" size="20" />
					<view class="amount">
						12
					</view>
				</view> -->
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
				swiperList:[1,1,1,1],
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
			previewImage(){
				uni.previewImage({
					urls:['https://img0.baidu.com/it/u=3862781436,3930243715&fm=253&fmt=auto&app=138&f=JPEG?w=690&h=460',
					'https://img0.baidu.com/it/u=3862781436,3930243715&fm=253&fmt=auto&app=138&f=JPEG?w=690&h=460',
					'https://img0.baidu.com/it/u=3862781436,3930243715&fm=253&fmt=auto&app=138&f=JPEG?w=690&h=460',
					'https://img0.baidu.com/it/u=3862781436,3930243715&fm=253&fmt=auto&app=138&f=JPEG?w=690&h=460',],
					current:this.currentIndex,
					
				})
			},
			onChange(e){
				let index = e.target.current || e.detail.current;
				this.currentIndex=index;
				console.log(index);
			},
			backTo(){
				uni.navigateBack({
					
				})
			}
		}
	}
</script>

<style lang="scss">
.idea {
	.nav_bar_top{
		z-index: 10;
		width: 100%;
		height: $uni-topbar-height-sm;
		background-color: #fff;
		position: fixed;
		top: 0;
	}
	.idea_navbar{
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
			margin-left: 20rpx;
			/* #ifdef MP-WEIXIN */
				margin-left: 0rpx;
			/* #endif */
			flex: 1;
			.input-uni-icon{
				margin-left: 20rpx;
			}
		}
		.add{
			font-size: 30rpx;
			color: coral;
		}
		.blogger_view{
			flex: 1;
			display: flex;
			height: 30px;
			margin-left: 20rpx;
			/* #ifdef MP-WEIXIN */
				width: 420rpx;
			/* #endif */
			image{
				width: 80rpx;
				height: 80rpx;
			}
			.name{
				font-weight: 600;
				margin-left: 20rpx;
				font-size: 28rpx;
				line-height: 80rpx;
			}
		}
	}
	swiper{
		margin-top: 180rpx;
		text-align: center;
		width: 100%;
		height: 500rpx;
		image{
			width: 97%;
			height: 90%;
		}
	}
	.idea_content{
		margin: 20rpx;
		color: #343434;
		font-size: 35rpx;
	}
	.issue_time{
		margin:30rpx 20rpx;
		font-size: 25rpx;
		color: gray;
	}
	.idea_bottom{
		text-align: center;
		color:gray;
		margin: 40rpx auto;
		padding-bottom: 50rpx;
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
			width: 200rpx;
			display: flex;
			margin-right: 20rpx;
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
