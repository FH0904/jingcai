<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	@font-face {
		font-family: AlphaH;
		src: url('./static/fonts/AlphaH.ttf');
	}
	/*每个页面公共css */
	page {
		height: 100%;
		font-size: 28upx;
		font-family: -apple-system,BlinkMacSystemFont,Segoe UI,Roboto,Helvetica Neue,Helvetica,PingFang SC,Hiragino Sans GB,Microsoft YaHei,SimSun,sans-serif;
		-webkit-font-smoothing: antialiased;
		font-style: normal;
		-moz-osx-font-smoothing: grayscale;
		background-color: #0c121f;
		box-sizing: border-box;
		color: #bacef1;
		text-align: center;
	}
	
	image {
		width: 100%;
	}
</style>
