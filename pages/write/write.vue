<template>
	<view class="write">
		<view class="nav_bar_top"></view>
		<uni-nav-bar class="write_navbar">
			    <block slot="left">
			    	<view @click="goBack">
			    		<uni-icons type="closeempty" color="#666" size="28" />
			    	</view>
			    </block>
		    <block slot="right">
				<view class="city" @click="scan">
					发布
				</view>
		    </block>
		</uni-nav-bar>
		<u-upload
				:fileList="fileList1"
				@afterRead="afterRead"
				@delete="deletePic"
				name="1"
				multiple
				:maxCount="10"
				:previewFullImage="true"
				width="210"
				height="210"
		></u-upload>
		<view class="content">
			<textarea auto-height="true" class="textarea"  value="" placeholder="写下你的想法" maxlength="-1"/>
		</view>
		<view class="bottom">
			<view class="bottom_item">
				#
			</view>
			<view class="bottom_item">
				@
			</view>
			<view class="bottom_item">
				<uni-icons type="location" color="#666" size="25" />
			</view>
			<!-- #ifdef MP-WEIXIN -->
			   <view class="fabu">
			   	发布
			   </view>
			<!-- #endif -->
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				fileList1: [],
			}
		},
		methods: {
			goBack(){
				uni.navigateBack({
					
				})
			},
			// 删除图片
			deletePic(event) {
				this[`fileList${event.name}`].splice(event.index, 1)
			},
			// 新增图片
			async afterRead(event) {
				// 当设置 mutiple 为 true 时, file 为数组格式，否则为对象格式
				let lists = [].concat(event.file)
				let fileListLen = this[`fileList${event.name}`].length
				lists.map((item) => {
					this[`fileList${event.name}`].push({
						...item,
						status: 'uploading',
						message: '上传中'
					})
				})
				for (let i = 0; i < lists.length; i++) {
					const result = await this.uploadFilePromise(lists[i].url)
					let item = this[`fileList${event.name}`][fileListLen]
					this[`fileList${event.name}`].splice(fileListLen, 1, Object.assign(item, {
						status: 'success',
						message: '',
						url: result
					}))
					fileListLen++
				}
			},
			uploadFilePromise(url) {
				return new Promise((resolve, reject) => {
					let a = uni.uploadFile({
						url: 'http://192.168.2.21:7001/upload', // 仅为示例，非真实的接口地址
						filePath: url,
						name: 'file',
						formData: {
							user: 'test'
						},
						success: (res) => {
							setTimeout(() => {
								resolve(res.data.data)
							}, 1000)
						}
					});
				})
			},
		}
	}
</script>

<style lang="scss">
.write{
	.nav_bar_top{
		z-index: 10;
		width: 100%;
		height: $uni-topbar-height-sm;
		background-color: #fff;
		position: fixed;
		top: 0;
	}
	.write_navbar{
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
			font-size: 31rpx;
			background-color: #8f80ff;
			padding: 0rpx 25rpx;
			height: 60rpx;
			line-height: 55rpx;
			border-radius: 40rpx;
			color: #fff;
		}
	}
	.u-upload{
		margin: 0 20rpx ;
		margin-top: 180rpx;
	}
	.content{
		margin: 10rpx 30rpx;
		.textarea{
			width: 100%;
			// height: 65vh;
		}
		
	}
	.bottom{
		z-index: 10;
		position: fixed;
		bottom: 0;
		width: 100%;
		color: gray;
		display: flex;
		font-size: 45rpx;
		padding: 0 30rpx;
		background-color: #fff;
		height: 100rpx;
		line-height: 100rpx;
		border-top: 1px solid #Eee;
		.bottom_item{
			margin: 0 40rpx;
		}
		.fabu{
			margin-top: 25rpx;
			margin-left: 200rpx;
			font-size: 31rpx;
			background-color: #8f80ff;
			padding: 0rpx 25rpx;
			height: 60rpx;
			line-height: 60rpx;
			border-radius: 40rpx;
			color: #fff;
		}
	}
}
</style>
