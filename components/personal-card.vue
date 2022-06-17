<template>
	<view class="follow_item">
		<image :src="(`${personalInfo.img}`)" mode=""></image>
		<view class="right">
			<view class="name">
				{{personalInfo.name}}
			</view>
			<view class="university">
				{{personalInfo.university}}
			</view>
		</view>
		<view class="button_follow" @click="noFollws">
		     <uni-icons v-show="personalInfo.isFollows" type="checkmarkempty" size="15" color="#999" />
			 {{personalInfo.isFollows?'互相关注':'关注'}}
		</view>
		<u-modal @confirm="clickTipYes" @cancel="clickTipNo" :show="tipShow" :showCancelButton="true" :title="title"></u-modal>
	</view>
</template>

<script>
	export default {
		name:"personal-card",
		props:{
			personalInfo:{
				type:Object
			}
		},
		data() {
			return {
				tipShow:false,
				title:'确定不再关注TA吗',
				noFollwsIndex:-1,
			};
		},
		methods:{
			noFollws(i){
				if(this.personalInfo.isFollows){
					this.title="确定不再关注TA吗"
				}else{
					this.title="确定要关注TA吗"
				}
				this.tipShow=true
				this.noFollwsIndex=i
			},
			clickTipYes(){
				// personalInfo.isFollows=!personalInfo.isFollows
				this.tipShow=false;
			},
			clickTipNo(){
				this.tipShow=false;
			}
		}
	}
</script>

<style lang="scss">
.follow_item{
			display: flex;
			margin: 20rpx 0;
			padding-bottom: 15rpx;
			border-bottom: 1rpx solid #d3d3d3;
			image{
				width: 150rpx;
				height: 150rpx;
				border-radius: 50%;
			}
			.right{
				width: 370rpx;
				display: flex;
				flex-direction: column;
				margin-left: 20rpx;
				margin-top: 35rpx;
				.name{
					// font-size: 35rpx;
					font-weight: 600;
					margin-bottom: 10rpx;
				}
				.university{
					color: #535353;
					font-size: 25rpx;
				}
			}
			.button_follow{
				font-size: 28rpx;
				margin-top: 40rpx;
				border: 1px solid #999;
				color:  #999;
				height: 40rpx;
				width: 140rpx;
				text-align: center;
				padding: 10rpx 20rpx;
				border-radius: 35rpx;
				/* #ifdef MP-WEIXIN */
					height: 60rpx;
					width: 180rpx;
				/* #endif */
			}
		}
</style>