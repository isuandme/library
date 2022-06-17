<template>
	<view class="member">
		<view class="top_wrap">
			<view class="person_wrap">
				<image src="https://img2.baidu.com/it/u=3973855039,4170930478&fm=253&fmt=auto&app=138&f=PNG?w=500&h=500" mode=""></image>
				<view class="name_wrap">
					<view class="name">
						吧唧一笑isrio
					</view>
					<view class="vip_level">
						至尊会员
					</view>
				</view>
				<view class="manage">
					续费管理
				</view>
			</view>
			<view class="date">
				有效期至 2023-01-05
			</view>
			<view class="renew">
				立即续费
			</view>
		</view>
		<view class="middle_bar">
			<view class="bar_item" v-for="(item,index ) in middleBarList" :key="index">
				<view class="title">
					{{item.tit}}
				</view>
				<view class="content">
					{{item.content}}
				</view>
			</view>
		</view>
		<swiper :autoplay="true" :interval="3000" :duration="1000">
			<swiper-item v-for="(item,index) in [0,0,0]" :key="index">
				<image src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.zcool.cn%2Fcommunity%2F019e275c3e99cba801213f269cf3ad.png%401280w_1l_2o_100sh.png&refer=http%3A%2F%2Fimg.zcool.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656323137&t=f4030ac656e9634641495311fe86e725" mode=""></image>
			</swiper-item>
		</swiper>
		<view class="member_power_wrap">
			<view class="title">
				会员特权
			</view>
			<view class="middle_bar">
				<view class="bar_item" v-for="(item,index ) in powerList" :key="index">
					<view class="title">
						<text class="iconfont" :class="item.icon"></text>
					</view>
					<view class="content">
						{{item.content}}
					</view>
				</view>
			</view>
		</view>
		<view class="member_power_wrap">
			<view class="title">
				视听臻享
			</view>
			<view class="video_wrap">
				<view class="video_item">
					<image src="https://img1.baidu.com/it/u=1275895507,934482785&fm=253&fmt=auto&app=120&f=JPEG?w=459&h=650" mode=""></image>
					<view class="name">
						《三体解说》
					</view>
				</view>
				<view class="video_item">
					<image src="https://img1.baidu.com/it/u=1275895507,934482785&fm=253&fmt=auto&app=120&f=JPEG?w=459&h=650" mode=""></image>
					<view class="name">
						《三体解说》
					</view>
				</view>
				<view class="video_item">
					<image src="https://img1.baidu.com/it/u=1275895507,934482785&fm=253&fmt=auto&app=120&f=JPEG?w=459&h=650" mode=""></image>
					<view class="name">
						《三体解说》
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
				middleBarList:[{
					tit:'会员积分',
					content:'20分'
				},{
					tit:'会员等级',
					content:'LV6 至尊会员'
				},{
					tit:'会员福利',
					content:'特权礼包'
				},],
				powerList:[{
					icon:'icon-qianbi1',
					content:'免押服务'
				},{
					icon:'icon-tushu',
					content:'订阅翻倍'
				},{
					icon:'icon-qunzuduoren',
					content:'多人预约'
				},{
					icon:'icon-voucher',
					content:'福利代金券'
				},]
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
.member{
	padding: 0 50rpx;
	.top_wrap{
		margin: 20rpx 0rpx;
		border-radius: 15rpx;
		box-shadow: 0 0 10rpx 5rpx #eee;
		.person_wrap{
			display: flex;
			image{
				flex: 1.2;
				width: 100rpx;
				height: 105rpx;
				margin: 10rpx 15rpx;
			}
			.name_wrap{
				flex: 4;
				display: flex;
				flex-direction: column;
				margin-top: 15rpx;
				.name{
					font-size: 35rpx;
					color: #bf6b37;
				}
				.vip_level{
					margin-top: 5rpx;
					font-size: 20rpx;
					width: 120rpx;
					text-align: center;
					padding: 5rpx 10rpx;
					background-color: #ff924a;
					color: #fff;
				}
			}
			.manage{
				font-size: 28rpx;
				margin-top: 20rpx;
				color: gray;
				flex:2;
			}
		}
		.date{
			display: inline-block;
			color: gray;
			margin: 0rpx 20rpx;
			font-size: 25rpx;
		}
		.renew{
			display: inline-block;
			text-align: center;
			display: inline-block;
			margin: 20rpx;
			margin-left: 170rpx;
			background-color: #ff924a;
			color: #fff;
			padding: 10rpx 20rpx;
			border-radius: 25rpx;
		}
	}
	.middle_bar{
		display: flex;
		margin: 30rpx 0rpx;
		.bar_item{
			flex: 1;
			display: flex;
			flex-direction: column;
			text-align: center;
			color: #676767;
			.title{
				
			}
			.content{
				margin-top: 15rpx;
				font-size: 28rpx;
			}
		}
	}
	swiper{
		margin: 10rpx 0rpx;
		height: 180rpx;
		image{
			width: 100%;
		}
	}
	.member_power_wrap{
		margin: 40rpx 0;
		padding: 20rpx;
		box-shadow: 0 0 10rpx 5rpx #eee;
		.iconfont{
			font-size: 60rpx;
			color: #ff924a;
		}
		.video_wrap{
			margin-top: 20rpx;
			display: flex;
			flex-wrap: wrap;
			.video_item{
				width: 180rpx;
				display: flex;
				flex-direction: column;
				margin: 10rpx;
				image{
					width: 180rpx;
					height: 200rpx;
				}
				.name{
					text-align: center;
					font-size: 28rpx;
					margin-top: 10rpx;
				}
			}
		}
	}
}
</style>
