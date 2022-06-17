<template>
	<view class="search_content">
		<view class="nav_bar_top"></view>
		<uni-nav-bar class="search_navbar" leftWidth="80rpx" rightWidth="50rpx" backgroundColor="#ff9238">
			   <block slot="left">
			   	   <view class="city" @click="backTo">
			   	   	   <uni-icons class="input-uni-icon" type="back" size="25" color="#ffffff" />
			   	   </view>
			   </block>
			
		    <view class="input-view">
		    	<uni-icons class="input-uni-icon" type="search" size="18" color="#999" />
		    	<input confirm-type="search" class="nav-bar-input" type="text" placeholder="输入搜索关键词" v-model="searchInfo" :focus="false" 
		    		@confirm="confirm" />
		    </view>
			<!-- #ifdef APP-PLUS || H5-->
			<block slot="right">
				<view class="city">
					<uni-icons class="input-uni-icon" type="more-filled" size="25" color="#fff" />
				</view>
			</block>
			<!-- #endif -->
		</uni-nav-bar>
		<view class="select_wrap">
			<view class="option_first" @click="change(0)" :class="current===0?'active':''">
				{{rank[currentRank]}} <uni-icons class="input-uni-icon" :type="isShow?'top':'bottom'" size="15" color="#000000" />
			</view>
			<view class="option_first" @click="change(1)" :class="current===1?'active':''">
				销量
			</view>
			<view class="down" :style="{'height': (height +'rpx')}">
				<view class="down_item" v-for="(item,index) in rank" :key="index" :class="currentRank===index?'active':''" @click="changeRank(index)">
					{{item}}
				</view>
			</view>
		</view>
		<!-- 遮罩层 -->
		<u-overlay :show="isShow" @click="isShow = false;height=0" >
		<view class="nav_bar_top"></view>
		<uni-nav-bar class="search_navbar" leftWidth="80rpx" rightWidth="50rpx" backgroundColor="#ff9238">
			   <block slot="left">
			   	   <view class="city" @click="backTo">
			   	   	   <uni-icons class="input-uni-icon" type="back" size="25" color="#ffffff" />
			   	   </view>
			   </block>
			
		    <view class="input-view">
		    	<uni-icons class="input-uni-icon" type="search" size="18" color="#999" />
		    	<input confirm-type="search" class="nav-bar-input" type="text" placeholder="输入搜索关键词" v-model="searchInfo" :focus="false" 
		    		@confirm="confirm" />
		    </view>
			<!-- #ifdef APP-PLUS || H5-->
			<block slot="right">
				<view class="city">
					<uni-icons class="input-uni-icon" type="more-filled" size="25" color="#fff" />
				</view>
			</block>
			<!-- #endif -->
		</uni-nav-bar>
		<view class="select_wrap">
			<view class="option_first" @click="change(0)" :class="current===0?'active':''">
				{{rank[currentRank]}} <uni-icons class="input-uni-icon" :type="isShow?'top':'bottom'" size="15" color="#000000" />
			</view>
			<view class="option_first" @click="change(1)" :class="current===1?'active':''">
				销量
			</view>
			<view class="down" :style="{'height': (height +'rpx')}">
				<view class="down_item" v-for="(item,index) in rank" :key="index" :class="currentRank===index?'active':''" @click="changeRank(index)">
					{{item}}
				</view>
			</view>
		</view>
		</u-overlay>
		
		<view class="search_result">
			<view class="result_wrap">
				<view @click="goDetail" class="result_item" v-for="(item,index) in searchContent" :key="index">
					<image src="https://img1.baidu.com/it/u=1275895507,934482785&fm=253&fmt=auto&app=120&f=JPEG?w=459&h=650" mode=""></image>
					<view class="name"><text class="iconfont icon-shuben1"></text>活着</view>
					<view class="price">
						<text>￥5</text>
						<view class="lendCount">
						    借阅次数 100
					    </view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				searchInfo:'全网找的四川女孩找到了',
				searchContent:[1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],
				current:0,
				isShow:false,
				height:0,
				currentRank:0,
				rank:['综合','押金升序','押金降序','借阅次数升序','借阅次数降序']
			}
		},
		methods: {
			backTo(){
				uni.navigateBack({
					
				})
			},
			confirm(){
				console.log('搜索');
			},
			change(i){
				this.current=i;
				if(i==0){
					this.isShow=!this.isShow
					if(this.isShow){
						setTimeout(()=>{
							this.height=370
							// #ifdef APP-PLUS
							    this.height=380
							// #endif
						},100)
					}
					else{
						this.height=0
					}
				}
			},
			changeRank(i){
				this.isShow=!this.isShow
				this.currentRank=i
				this.opacity = 0
				this.height=0
			},
			goDetail(){
				console.log('gogo');
				uni.navigateTo({
					url:'../book_detail/book_detail'
				})
			}
		}
	}
</script>

<style lang="scss">
.search_content{
	display: flex;
	.nav_bar_top{
		z-index: 10;
		width: 100%;
		height: 80rpx;
		/* #ifdef MP-WEIXIN */
		   height: 100rpx;
		/* #endif */
		background-color: #ff9238;
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
	.select_wrap{
		z-index: 11;
		position: fixed;
		top: 140rpx;
		left: 0;
	    /* #ifdef MP-WEIXIN */
	        top:173rpx;
	    /* #endif */
	    display: flex;
		padding: 25rpx  15rpx;
		width: 100%;
	    background-color: #ffffff;
		border-bottom: 1px solid #ececec;
	    .option_first{
			text-align: center;
	    	width: 50%;
			.input-uni-icon{
				margin-left: 10rpx;
			}
	     }
		 .active{
			 color: #ff9238;
			 .input-uni-icon{
			     color: #ff9238 !important;
			  }
		 }
		 .down{
			 background-color: #ffffff;
			 position: absolute;
			 top: 94rpx;
			 left: 0;
			 width: 93.8%;
			 padding: 0 10rpx;
			 border-radius: 0 0 15rpx 15rpx;
			 height: 0rpx;
			 overflow: hidden;
			 transition: all .5s;
			 /* #ifdef MP-WEIXIN */
			      top: 90rpx;
				  width: 100%;
			 /* #endif */
			 .down_item{
				 margin: 10rpx auto;
				 padding: 10rpx 0;
				 border-bottom: 1px solid #eee;
				 
			 }
			 .active{
				 color: #ff9238;
			 }
			 .down_item:last-child{
				 border-bottom: none;
			 }
		 }
	}
    .search_result{
		margin: 150rpx auto;
		padding: 0 15rpx;
	    // margin-top: 150rpx;
	    width: 100%;
		border-radius: 20rpx;
		.result_wrap{
				display: flex;
				flex-wrap: wrap;
				width: 100%;
				margin-top:100rpx;
				/* #ifdef MP-WEIXIN */
				    margin-top:140rpx;
				/* #endif */
				.result_item{
					box-sizing: border-box;
					// border: 1px solid #dfdfdf;
					box-shadow: 0 0 10rpx 5rpx #f5f5f5;
					margin: 15rpx;
					width: 45%;
					border-radius: 15rpx;
					image{
						width: 80%;
						height: 300rpx;
						margin: 0rpx 30rpx;
						// border-radius: 15rpx;
					}
					.name{
						margin: 5rpx 0;
						margin-left: 35rpx;
						font-weight: 700;
						.iconfont{
							font-size: 40rpx;
							margin-right: 20rpx;
							color: #ff9238;
						}
					}
					.price{
						font-size: 30rpx;
						margin: 10rpx 0;
						margin-left: 30rpx;
						text{
							color: #ff9238;
						}
					    .lendCount{
							// float: right;
					    	margin-left: 50rpx;
					    	display: inline-block;
					    	font-size: 25rpx;
					    	color: gray;
					    }
					}
					
				}
		}
			
	}
	
}
</style>
