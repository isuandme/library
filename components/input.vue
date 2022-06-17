<template>
	<view class="input-view">
		<uni-icons class="input-uni-icon" type="search" size="18" color="#999" />
		<input confirm-type="search" class="nav-bar-input" type="text" :placeholder="text" disabled
			@click="toSearch" />
	</view>
</template>

<script>
	export default {
		name:"input",
		props:{
			text:{
				type:String
			}
		},
		data() {
			return {
				
			};
		},
		methods:{
			toSearch(){
				uni.navigateTo({
					url:'../search/search'
				})
			},
		}
	}
</script>

<style lang="scss">
.input-view{
		background-color: #f8f8f8;
		height: 30px;
		border-radius: 15px;
		padding: 0px 15px;
		margin: 7px 0;
		line-height: 30px;
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
			font-size: 25rpx;
		}
	}
</style>