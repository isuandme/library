<template>
	<view class="mYFans">
		<my-input :text="text"></my-input>
		<view class="" v-if="followLists.length>0">
			<view class="fans_wrap" v-for="(item,index ) in followLists " :key="index">
				<person-card :personalInfo="item"></person-card>
			</view>
		</view>
		<view class="icon" v-else>
			<text class="iconfont icon-null"></text>
			<view class="">
				还没有粉丝噢~
			</view>
		</view>
	</view>
</template>

<script>
	import MyInput from '../../components/input.vue'
	import PersonCard from '../../components/personal-card.vue'
	export default {
		components:{
			PersonCard,
			MyInput
		},
		data() {
			return {
				text:'搜索全部粉丝',
				followLists:[
					// {
					// 	name:'张三',
					// 	img:'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fc-ssl.duitang.com%2Fuploads%2Fblog%2F202104%2F18%2F20210418222738_0160c.thumb.1000_0.jpg&refer=http%3A%2F%2Fc-ssl.duitang.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656480958&t=5a25d267e2f56655c7159a5c7b8874a3',
					// 	university:'西南石油大学',
					// 	isFollows:true
					// },{
					// 	name:'李四',
					// 	img:'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fup.enterdesk.com%2Fedpic_source%2Fff%2F0b%2F6d%2Fff0b6d250839a43eadab5e759dc4338c.jpg&refer=http%3A%2F%2Fup.enterdesk.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656480958&t=35ad9fae6c26e75d6171d499d49cf71c',
					// 	university:'西南石油大学',
					// 	isFollows:true
					// },{
					// 	name:'王一博',
					// 	img:'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fup.enterdesk.com%2Fedpic%2Fcb%2F9f%2Fbc%2Fcb9fbccaf2a6814994df8d5e72b82b1c.jpg&refer=http%3A%2F%2Fup.enterdesk.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656480958&t=2d102bd4a66623ac6da06b00563be39b',
					// 	university:'西南石油大学',
					// 	isFollows:true
					// },{
					// 	name:'肖战',
					// 	img:'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fup.enterdesk.com%2Fedpic_source%2F33%2F6d%2F82%2F336d82ec4a3fc5cf5add5c347946452e.jpg&refer=http%3A%2F%2Fup.enterdesk.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656480958&t=97a0ebd5057e3b695c131b0aa53efb09',
					// 	university:'重庆工商大学',
					// 	isFollows:true
					// },{
					// 	name:'王五',
					// 	img:'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fup.enterdesk.com%2Fedpic%2Feb%2F24%2Fd5%2Feb24d54a0c4e1f174a7a4922aaa28454.jpg&refer=http%3A%2F%2Fup.enterdesk.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656480958&t=c08c835b5c6401843fb149e8ffd11923',
					// 	university:'西南石油大学',
					// 	isFollows:true
					// },{
					// 	name:'赵六',
					// 	img:'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fup.enterdesk.com%2Fedpic_source%2F30%2F90%2F40%2F309040a0602c672cebc6ab3a1bbbc8cd.jpg&refer=http%3A%2F%2Fup.enterdesk.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656480958&t=8b51be101393048f533554ef864ec673',
					// 	university:'西南石油大学',
					// 	isFollows:true
					// },{
					// 	name:'赵六',
					// 	img:'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fup.enterdesk.com%2Fedpic_source%2F30%2F90%2F40%2F309040a0602c672cebc6ab3a1bbbc8cd.jpg&refer=http%3A%2F%2Fup.enterdesk.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656480958&t=8b51be101393048f533554ef864ec673',
					// 	university:'西南石油大学',
					// 	isFollows:true
					// },{
					// 	name:'赵六',
					// 	img:'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fup.enterdesk.com%2Fedpic_source%2F30%2F90%2F40%2F309040a0602c672cebc6ab3a1bbbc8cd.jpg&refer=http%3A%2F%2Fup.enterdesk.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656480958&t=8b51be101393048f533554ef864ec673',
					// 	university:'西南石油大学',
					// 	isFollows:true
					// },{
					// 	name:'赵六',
					// 	img:'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fup.enterdesk.com%2Fedpic_source%2F30%2F90%2F40%2F309040a0602c672cebc6ab3a1bbbc8cd.jpg&refer=http%3A%2F%2Fup.enterdesk.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656480958&t=8b51be101393048f533554ef864ec673',
					// 	university:'西南石油大学',
					// 	isFollows:true
					// },{
					// 	name:'赵六',
					// 	img:'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fup.enterdesk.com%2Fedpic_source%2F30%2F90%2F40%2F309040a0602c672cebc6ab3a1bbbc8cd.jpg&refer=http%3A%2F%2Fup.enterdesk.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1656480958&t=8b51be101393048f533554ef864ec673',
					// 	university:'西南石油大学',
					// 	isFollows:true
					// },
				]
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
.mYFans{
	margin: 20rpx ;
	.fans_wrap{
		// margin: 20rpx ;
	}
	.icon{
		text-align: center;
		margin: 100rpx 0;
		.iconfont{
			font-size: 280rpx;
			color: #666;
		}
		
	}
}
</style>
