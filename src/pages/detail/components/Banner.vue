<template>
<div>
	<div class="banner" @click="handleBannerClick">
		<img class="banner-img" :src="bannerImg" alt="">
		<div class="banner-info">
			<div class="banner-title">{{this.sightName}}</div>
			<div class="banner-number"><span class="iconfont banner-icon">&#xe632;</span>{{this.bannerImgs.length}}</div>
		</div>
	</div>
	<fade-animation>
	<common-gallary :imgs='bannerImgs' v-show="showGallery" @close='handleGalleryClose'></common-gallary>
	</fade-animation>
	</div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary'
import FadeAnimation from 'common/fade/FadeAnimation'
	export default{
		name:'DetailBanner',
		props:{
			sightName:String,
			bannerImg:String,
			bannerImgs:Array
		},
		data(){
			return{
				showGallery:false
			}
		},
		components:{
			CommonGallary,
			FadeAnimation
		},
		methods:{
			handleBannerClick(){
				this.showGallery=true
			},
			handleGalleryClose(){
				this.showGallery=false
			}
		}
	}
</script>

<style lang="stylus" scoped="scoped">
	.banner
		overflow hidden
		height 0
		padding-bottom 55%
		position relative
		.banner-img
			width 100%
		.banner-info
			position absolute
			left  0
			right 0
			bottom 0
			line-height .6rem
			display flex
			color #fff
			background-image linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,.8))
			.banner-title
				flex 1
				font-size .32rem
				padding 0 .2rem
			.banner-number
				padding 0 .4rem
				margin-top .14rem
				line-height .32rem
				height .32rem
				border-radius .2rem
				background rgba(0,0,0,.8)
				font-size .24rem
				.banner-icon
					font-size .24rem
</style>
