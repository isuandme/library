<template>
	<view class="search">
		<view class="nav_bar_top"></view>
		<uni-nav-bar class="search_navbar" leftWidth="65rpx">
			   <block slot="left">
			   	   <view class="city" @click="backTo">
			   	   	   <uni-icons class="input-uni-icon" type="back" size="25" color="#999" />
			   	   </view>
			   </block>
			
		    <view class="input-view">
		    	<uni-icons class="input-uni-icon" type="search" size="18" color="#999" />
		    	<input confirm-type="search" class="nav-bar-input" type="text" placeholder="输入搜索关键词" v-model="searchInfo" :focus="isFoucus"
		    		@confirm="confirm" />
		    </view>
			<!-- #ifdef APP-PLUS || H5-->
			<block slot="right">
				<view class="city" @click="cancel">
					<text>取消</text>
				</view>
			</block>
			<!-- #endif -->
		</uni-nav-bar>
		<view class="guessContent">
			<view class="guess_top">
				<view class="guessSearch">
					猜你想搜
				</view>
				<view class="change">
			   	   	<uni-icons class="input-uni-icon" type="loop" size="15" color="#999" />
					换一换
				</view>
			</view>
			<view class="guessSearch_key">
				<view class="" @click="goDetail(1)">
					全网找的四川女孩找到了找到了
				</view>
				<view class="">
					全网找的四川女孩找到了
				</view>
				<view class="">
					全网找的四川女孩找到了
				</view>
				<view class="">
					全网找的四川女孩
					<text class="iconfont icon-bao"></text>
				</view>
				<view class="">
					全网找的四川<text class="iconfont icon-xin"></text>
				</view>
				<view class="">
					全女孩找到了
				</view>
			</view>
		    <view class="hot_no">
		    	<view class="hot_title">
		    		热榜
		    	</view>
				<view class="hot_content">
					<view class="hot_content_item"><text class="iconfont icon-redian"></text>于凌晨走丢的袁花花已经找到</view>
					<view class="hot_content_item"><text class="iconfont icon-redian"></text>于凌晨走丢的袁花花已经找到</view>
					<view class="hot_content_item"><text class="iconfont icon-redian"></text>于凌晨走丢的袁花花已经找到</view>
					<view class="hot_content_item"><text class="iconfont icon-redian"></text>于凌晨走丢的袁花花已经找到</view>
					<view class="hot_content_item"><text class="iconfont icon-redian"></text>于凌晨走丢的袁花花已经找到</view>
					<view class="hot_content_item"><text>4</text>于凌晨走丢的袁花花已经找到</view>
					<view class="hot_content_item"><text>5</text>于凌晨走丢的袁花花已经找到</view>
					<view class="hot_content_item"><text>6</text>于凌晨走丢的袁花花已经找到</view>
					<view class="hot_content_item"><text>7</text>于凌晨走丢的袁花花已经找到</view>
					<view class="hot_content_item"><text>8</text>于凌晨走丢的袁花花已经找到</view>
					<view class="hot_content_item"><text>9</text>于凌晨走丢的袁花花已经找袁花花已经找到袁花花已经找到到</view>
					<view class="hot_content_item"><text>10</text>于凌晨走丢的袁花花已经找到</view>
					<view class="hot_content_item"><text>11</text>于凌晨走丢的袁花花已经找到</view>
					<view class="hot_content_item"><text>12</text>于凌晨走丢的袁花花已经找到</view>
				</view>
		    </view>
		</view>
		<!-- <view class="searchContent">
	    	<view class="content_item" v-for="(item,index) in searchContent" :key="index" @click="goDetail(index)">
				<uni-icons type="notification" color="#ffb64f" size="18" />
	    		<text>前端运行日志，请另行在小程序开发</text>
	    	</view>
	    </view> -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				isFoucus:true,
				searchInfo:'',
				searchContent:[1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],
			}
		},
		methods: {
			backTo(){
				uni.navigateBack({
					
				})
			},
			cancel(){
				this.isFoucus=false;
				this.searchInfo='';
			},
			confirm(){
				console.log('搜索');
			},
			goDetail(i){
				uni.navigateTo({
					url:'../search_content/search_content?id='+45
				})
			}
		}
	}
</script>

<style lang="scss">
.search{
	display: flex;
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
	.search_navbar{
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
    .searchContent{
		margin-top: 170rpx;
		width: 100%;
		border-radius: 15rpx 15rpx;
		box-shadow: 0 0  10px 5px #ebebeb;
		.content_item{
			color: #878787;
			padding: 20rpx 0rpx;
			margin: 0 20px;
			margin-left: 10rpx;
			border-bottom: 1px solid #878787;
			text{
				margin-left: 20rpx;
			}
		}
		.content_item:last-child{
			border-bottom: none;
		} 
	}
	.guessContent{
		margin: 0 35rpx;
		margin-top: 155rpx;
		color: gray;
		width: 100%;
		/* #ifdef MP-WEIXIN */
		margin-top: 175rpx;
		/* #endif */
		.guess_top{
			width: 100%;
			display: flex;
			justify-content: space-between;
			view{
				margin: 5rpx 0;
			}
			.guessSearch{
				color: #000;
			}
		}
		.guessSearch_key{
			width: 100%;
			margin: 10rpx 0;
			display: flex;
			flex-wrap: wrap;
			view{
				width: 48%;
				overflow: hidden;    
				text-overflow: ellipsis;    
				white-space: nowrap;
				margin: 15rpx 0;
				margin-right: 5rpx;
				text{
					color: red;
					margin-left: 5rpx;
				}
			}
		}
		.hot_no{
			margin-top: 20rpx;
			width: 100%;
			.hot_title{
				background: linear-gradient(red,orange);
				-webkit-background-clip: text;
				background-clip: text;
				color: transparent;
				font-weight: 700;
				font-size: 35rpx;
			}
			.hot_content{
				margin: 15rpx auto;
				padding: 15rpx;
				// background-color: #ffefef;
				box-shadow: 0 0  5rpx 5rpx #ebebeb;
				border-radius: 20rpx;
				.hot_content_item{
					width: 580rpx;
					margin: 30rpx 0;
					overflow: hidden;    
					text-overflow: ellipsis;    
					white-space: nowrap;
					text{
						margin: 0 10rpx;
						color: red;
						padding: 0 10rpx;
					}
				}
			}
		}
	}
}
</style>
