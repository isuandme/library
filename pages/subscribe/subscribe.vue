<template>
	<view class="subscribe">
		<view class="topbar">
			<view class="left">
				<text class="iconfont icon-hi"></text>
				欢迎
			</view>
			<view class="right">
				<text>西南石油大学图书馆</text>
				<uni-icons class="input-uni-icon" type="location" size="15" color="#999" />
			</view>
		</view>
		<view class="swiper_wrap">
		        <u-swiper
		                :list="list3"
		                previousMargin="70"
		                nextMargin="70"
		                :circular="false"
		                :autoplay="false"
		                radius="5"
		                bgColor="#ffffff"
						:current="cIndex"
						height="320rpx"
						@change="changeSwiper"
		        ></u-swiper>
		</view>
		<view class="introduce_wrap">
			<view class=" iconfont icon-huobao"></view>
			<view class="">{{introduceList[cIndex].name}}</view>
			<view class="">地点：{{introduceList[cIndex].add}}</view>
			<view class="tag">
			    <u-tag v-for="(item,index) in introduceList[cIndex].tab" :key="index" :text="item" size="mini" class="tag_item" type="warning" plain plainFill></u-tag>
			</view>
		</view>
		
		<view class="select_seat_wrap">
			<view class="date_wrap">
				<view class="date_option"
				    v-for="(item,index) in positionList" :key="index"
				    :class="index===currentItem?'active':''"
				    @click="seletedPosition(index)">
				    	今天{{item.position}}
				</view>
			</view>
			<view class="time_wrap">
				<view class="left_wrap">
					{{positionList[currentItem].position.split('.')[0]}}月{{positionList[currentItem].position.split('.')[1]}}日
				</view>
				<view class="right_wrap" @click="selectTiem" >
					<u-picker itemHeight="88" :show="show" :columns="columns" :closeOnClickOverlay="true" @change='changeSelect' @cancel="clickCancle" @confirm="clickYes()"></u-picker>
					  {{columns[0][currentColumn]}}
					<uni-icons class="input-uni-icon" type="bottom" size="15" color="#000000" />
				</view>
			</view>
			<view class="seat_info">
				<view class="seat_item" v-for="(item,index) in seat" :key="index">
					<text @click="clickSeat(index,index2)" v-for="(item2,index2) in item" 
					      :key="index2" class="iconfont" :class=" {'icon-kexuanzuowei':item2===0,'icon-yixuanzuowei':item2===1, 'icon-yixuanzuowei4':item2===-1,'icon-yixuanzuowei6':item2===2}" 
						  :style="{color:(item2===2?'#068b06':'')}">
						  
						  </text>
				</view>
				<view class="seat_option_info">
					<view class="info_item">
						<text  class="iconfont icon-kexuanzuowei"></text>
						可预约
					</view>
					<view class="info_item">
						<text  class="iconfont icon-yixuanzuowei"></text>
						已预约
					</view>
					<view class="info_item">
						<text  class="iconfont icon-yixuanzuowei no"></text>
						不可选
					</view>
				</view>
			</view>
			
			
		</view>
		<!-- #ifdef MP-WEIXIN -->
		<button @click="tipShow = true" class="subBitton" >预约</button>
		<!-- #endif -->
		<u-button @click="tipShow = true" class="subBitton" type="primary" shape="circle" text="预约" :plain="true" color="#006f00"></u-button>
		<view >
		     <u-modal @confirm="clickTipYes" :show="tipShow" :title="title" :content='content'></u-modal>
		</view>
		<!-- #ifdef MP-WEIXIN -->
		   <TabBar :current-page="2" />
		<!-- #endif -->
    </view>
</template>

<script>
	export default {
		data() {
			return {
				tipShow:false,
				title:'预约成功',
				content:'请按时到达，迟到半个小时以上将自动取消，详情请在我的预约查看。',
				list3: [
				    'https://cdn.uviewui.com/uview/swiper/swiper3.png',
				    'https://cdn.uviewui.com/uview/swiper/swiper2.png',
				    'https://cdn.uviewui.com/uview/swiper/swiper1.png',
				    'https://cdn.uviewui.com/uview/swiper/swiper3.png',
				    'https://cdn.uviewui.com/uview/swiper/swiper2.png',
				    'https://cdn.uviewui.com/uview/swiper/swiper1.png',
				],
				cIndex:0,
				introduceList:[{
					name:'星巴克咖啡厅',
					add:"图书馆一楼",
					tab:['美食','休闲','办公','会议']
				},{
					name:'计算机科学图书借阅区',
					add:"图书馆五楼",
					tab:['学习','休闲','办公','会议']
				},{
					name:'电气自动化图书借阅区',
					add:"图书馆二楼",
					tab:[ '办公','会议']
				},{
					name:'研修室',
					add:"图书馆11楼",
					tab:['学习','休闲','办公','会议']
				},{
					name:'法学图书借阅区',
					add:"图书馆三楼",
					tab:['休闲','办公','会议']
				},{
					name:'石油与天然气图书借阅区',
					add:"图书馆10楼",
					tab:['休闲','学学习','会议']
				}],
				currentItem:0,
				positionList:[
					{
						position:'5.17',
						readingAmount:120,
						remainCount:15
					},
					{
						position:'5.18',
						readingAmount:10,
						remainCount:150
					},
					{
						position:'5.19',
						readingAmount:100,
						remainCount:19
					}
				],
				show: false,
				currentColumn:0,
				columns: [
				    ['上午 8:00-11:30', '下午 12:00-17:00', '晚上 17:30-22:00']
				],
				seat:[
					[0,0,0,0,0,0,0,0],
					[0,0,0,0,0,0,0,0],
					[0,0,0,0,0,0,0,0],
					[0,0,0,0,0,0,0,0],
					[0,0,0,0,0,2,0,0],
					[0,0,0,0,0,1,0,0],
					[-1,0,0,0,0,0,0,-1],
				],
				currentSeat:-1
			}
		},
		methods: {
			changeSwiper(e){
				this.cIndex = e.current;
			},
			seletedPosition(i){
				this.currentItem=i;
			},
			selectTiem(){
				this.show= true;
			}
			,clickYes(){
				this.show=false;
			},
			clickTipYes(){
				this.tipShow=false;
			},
			clickCancle(){
				this.show=false;
			},
			changeSelect(e){
				console.log(e);
				this.currentColumn=e.index;
			},
			clickSeat(i1,i2){
				this.seat[i1][i2]= 2
				console.log(this.seat[i1][i2]);
			}
		}
	}
</script>

<style lang="scss">
.subscribe{
	.topbar{
		font-size: 28rpx;
		color: gray;
		display: flex;
		justify-content: space-between;
		padding: 10rpx 15rpx;
		.left{
			color: #000;
			text{
				font-size: 40rpx;
				color: #0099ff;
				margin-right: 5rpx;
			}
		}
		.right{
			text{
				margin-right: 10rpx;
			}
		}
	}
	.swiper_wrap{
		margin-top: 20rpx;
	}
	.introduce_wrap{
		position: relative;
		margin: 25rpx auto;
		width: 80%;
		padding: 25rpx;
		text-align: center;
		box-shadow: 0 0 10rpx 5rpx #eee;
		// background-color: #c7c7c7;
		border-radius: 15rpx;
		view{
			margin: 15rpx 0;
		}
		.iconfont{
			color: red;
			font-size:60rpx;
			position: absolute;
			top: -30rpx;
		}
		.tag{
			display: flex;
			justify-content: center;
			margin-top: 20rpx;
			.tag_item{
				margin: 0 8rpx;
			}
		}
	}
	.select_seat_wrap{
		width: 90%;
		margin: 10rpx auto;
		font-size: 28rpx;
		.date_wrap{
		    display: flex;
			margin-left: 5rpx;
			.date_option{
				margin-right: 1rpx;
				padding: 4rpx 25rpx;
				border: 1px solid #313131;
				border-radius: 0 15rpx 0rpx 0;
				border-bottom: none;
				transition: all .4s;
			}
			.active{
				background-color: #068b06;
				color: #fff;
			}
		}
		.time_wrap{
			// margin: 25rpx 0rpx;
			box-sizing: border-box;
			// width: 680rpx;
			width: 100%;
			padding: 10rpx 20rpx;
			font-weight: 700;
			display: flex;
			justify-content: space-between;
			box-shadow: 0 0 5rpx 1rpx #eee;
			.left_wrap{
				
			}
			.right_wrap{
				
				.input-uni-icon{
					margin-left: 10rpx;
				}
			}
		}
		.seat_info{
			margin-top: 0rpx;
			box-sizing: border-box;
			// width: 680rpx;
			width: 100%;
			background-color: #ffffff;
			border: 1rpx solid #eee;
			padding: 20rpx 10rpx;
			text-align: center;
			.seat_item{
				.iconfont{
					color: coral;
					font-size: 60rpx;
				}
				.icon-yixuanzuowei4{
					color: #6b6b6b;
				}
				.icon-yixuanzuowei6{
					color: #068b06;
				}
			}
			.seat_option_info{
				margin-top: 20rpx;
				display: flex;
			}
			.info_item{
				flex: 1;
				margin: 0 20rpx;
				.iconfont{
					font-size: 60rpx;
					margin: 0 10rpx;
					color: coral;
				}
				.no{
					color: #6b6b6b;
				}
			}
		}
	}
	.subBitton{
		width: 80%;
		font-weight: 700;
		margin-top: 35rpx;
		
		/* #ifdef MP-WEIXIN */
			margin-bottom: 150rpx;
			color: #068b06;
		    background-color: #fff;
		/* #endif */
	}
}
</style>
