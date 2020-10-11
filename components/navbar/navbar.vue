<template>
	<view class="navbar">
		<!-- 自定义导航栏 -->
		
		<view class="navbar-fiexd">
			<!-- 状态栏 -->
			<view :style="{height: statusBarHeight+'px'}">
				
			</view>
			<!-- 导航栏 -->
			<view class="navbar-content" :style="{height:navBarHeight+'px',width:windowWidth+'px'}">
				<view class="navbar-search">
				<view class="navbar-search_icon">
					<uni-icons type="search" size="16" color="#999"></uni-icons>
				</view>
				<view class="navbar-search_text">
					
				</view> 
				</view>
			</view>
			
		</view>
		
		<view style="{height: :statusBarHeight+navBarHeight+'px;;}">
			
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				statusBarHeight: 20,
				navBarHeight:45,
				windowWidth:375
			}
		},
		created() {
		 const info =	uni.getSystemInfoSync();
		 this.statusBarHeight =info.statusBarHeight
		 this.windowWidth = info.windowWidth
		 console,log(info)
		 //#ifndef H5||APP-PLUS||MP-ALIPAY
		 //获取胶囊位置
		const menuButtonInfo= uni.getMenuButtonBoundingClientRect()
		this.navBarHeight = (menuButtonInfo.bottom-info.statusBarHeight) +(menuButtonInfo.top - info.statusBarHeight)
		this.windowWidth = menuButtonInfo.left
		//#endif
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
	@import '../../common/css/icons.css';
	.navbar{
		.navbar-fiexd{
			position: fixed;
				top: 0;
				left: 0;
				z-index: 99;
				width: 100%;
				background-color: $mk-base-color;
				.navbar-content{
					height: 45px;
					padding: 0 15px;
					box-sizing: border-box;
					display: flex;
					justify-content: center;
					align-items: center;
					.navbar-search{
								display: flex;
								align-items: center;
								padding: 0 10px;
								width: 100%;
								height: 30px;
								padding: 0 10px;
								border-radius: 30px;
								background-color: #fff;
								.navbar-search_icon{
									
									margin-right: 10px;
								}
								.navbar-search_text{
									font-size: 12px;
									color: #999;
							}
						
						}
					}
				}
				
		
}
</style>