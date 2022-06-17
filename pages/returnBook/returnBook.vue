<template>
	<view class="returnBook">
		<uni-calendar :lunar="true" class="uni-calendar--hook" :selected="info.selected" :showMonth="false" @change="change" @monthSwitch="monthSwitch" />
	    <view class="return_wrap">
	    	<view class="option_wrap">
	    		<view class="option"  v-for="(item,index) in op" :key="index" 
				:class="currentIndex===index?'active':''"  @click="changeIndex(index)">
	    			{{item}}
	    		</view>
	    	</view>
			<view class="content_wrap">
				<view class="content_item" v-for="(item,index) in book_list" :key="index">
					<image src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg4.duitang.com%2Fuploads%2Fitem%2F201201%2F17%2F20120117144659_CEEuu.thumb.700_0.jpg&refer=http%3A%2F%2Fimg4.duitang.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1654761703&t=3da0cf622bcd081219c3d8c7ca36877f" mode=""></image>
					<view class="right">
						<view class="book_name">
							《三体》
						</view>
						<view class="date">
							有效期至 2022-06-01 
						</view>
						<view class="position">
							<uni-icons type="location" color="#666" size="14" />
							<text>三楼A区5号书架1-2</text>
						</view>
						<view class="option">
							<view class="option_wrap" @click="returnBook">
								提前归还
							</view>
							<view class="option_wrap" @click="postpone">
								延期续订
							</view>
						</view>
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
						书籍<text>5-1</text>
					</view>
				</view>
				<view class="book_position_wrap subscribe_wrap">
					<view class="title">
						延期至
					</view>
					<view class="example-body">
						<uni-datetime-picker type="date" @change="maskChange"  :start="start"/>
					</view>
				</view>
				<view class="comfirm">
					<button class="active" @click="comfirmBorrow">确认</button>
				</view>
		     </view>
			 <u-toast ref="uToast"></u-toast>
		</u-popup>
		<view>
		     <u-modal @confirm="clickTipYes" :show="tipShow" :title="title" :content='tipContent'></u-modal>
		</view>
		<view>
		     <u-modal @confirm="clickTipYes" :show="tipShow2" :showCancelButton="false" :title="title2"></u-modal>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				start: Date.now(),
				dateSelect:false,
				tagList:['少儿','魔法','冒险'],
				isShow:false,
				cell0:{
					message:'请选择日期',
					duration:800
				},
				tipShow:false,
				title:'延期成功',
				tipContent:'请在规定时间内还书。',
				
				info: {
				    selected: [{
						date: '2022-05-30',
						info: '即将到期'
					}]
				},
				op:['借阅归还','超时未还'],
				currentIndex:0,
				book_list:[1,2,3,4],
				tipShow2:false,
				title2:'归还成功',
			}
		},
		methods: {
			change(e) {
				console.log('change 返回:', e)
				// 模拟动态打卡
				// if (this.info.selected.length > 5) return
				// this.info.selected.push({
				// 	date: e.fulldate,
				// 	info: '打卡'
				// })
			},
			monthSwitch(e) {
				console.log('monthSwitchs 返回:', e)
			},
			changeIndex(i){
				this.currentIndex=i;
			},
			postpone(){
				this.isShow=true
			},
			close(){
				this.isShow=false
			},
			comfirmBorrow(){
				if(this.dateSelect){
					this.tipShow=true;
				}
				else{
					const params = this.cell0
					this.$refs.uToast.show({
						...params
					})
				}
			},
			maskChange(e){
				this.dateSelect= !this.dateSelect
				console.log(e);
			},
			clickTipYes(){
				this.tipShow=false;
				this.tipShow2=false;
			},
			returnBook(){
				this.tipShow2=true
			}
		}
	}
</script>

<style lang="scss">
.returnBook{
	.return_wrap{
		margin:40rpx 30rpx;
		.option_wrap{
		    display: flex;
			margin-left: 5rpx;
			.option{
				margin-right: 1rpx;
				padding: 4rpx 25rpx;
				border: 1px solid #e7e7e7;
				border-radius: 0 15rpx 0rpx 0;
				border-bottom: none;
				transition: all .4s;
			}
			.active{
				background-color: #8dc6da;
				color: #fff;
			}
		}
		.content_wrap{
			box-shadow: 0 0 10rpx 5rpx #eee;
			.content_item{
				display: flex;
				padding: 10rpx;
				border-bottom: 1px solid #eee;
				image{
					flex: 1;
					// width: 180rpx;
					height: 210rpx;
					margin: 10rpx;
				}
				.right{
					flex: 2.7;
					display: flex;
					flex-direction: column;
					text-align: center;
					margin-top: 10rpx;
					line-height: 48rpx;
					.book_name{
						font-weight: 600;
						
					}
					.date{
						color: #e55a09;
						font-size: 25rpx;
					}
					.position{
						color: gray;
						font-size: 25rpx;
					}
					.option{
						font-size: 28rpx;
						margin-top: 10rpx;
						
						.option_wrap{
							display: inline-block;
							padding: 0rpx 15rpx;
							border-radius: 15rpx;
							border: 1px solid #d8d8da;
						}
						.option_wrap:last-child{
							margin-left: 50rpx;
						}
					}
				}
			}
			.content_item:last-child{
				border-bottom: none;
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
