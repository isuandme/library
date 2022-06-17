
<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
			uni.onTabBarMidButtonTap(()=>{
				    console.log('点击');
					uni.navigateTo({
						url: '../subscribe/subscribe'
					});
			   }
			)
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style lang="scss">
	@import "@/uni_modules/uview-ui/index.scss";
	@import url('static/iconclass/icon.css');
</style>
