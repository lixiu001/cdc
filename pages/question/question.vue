<template>
	<view class="reserveShowroom">
		<img src="/static/seatBack.png" alt="" class="backimg"/>
		<view class="content">
			<div class="item" @click="jump(1)">
				<img src="/static/chakanzige.png" alt="" />
				<span>查看领奖资格</span>
			</div>
			<div class="item" @click="jump(2)">
				<img src="/static/lijidati.png" alt="" />
				<span>立即答题</span>
			</div>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			
		};
	},
	methods: {
		jump(data){
			let pageMap = {
				1: '/pages/qualification/qualification',
				2: '/pages/answer/answer',
			}
			uni.navigateTo({url: pageMap[data]})
		}
	}
}
</script>

<style lang="scss" scoped>
.reserveShowroom{
	width: 100%;
	height: 100vh;
	display: flex;
	flex-direction: column;
	align-items: center;
	.backimg{
		position: absolute;
		width: 100%;
		height: 100%;
	}
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		.item {
			position: relative;
			display: flex;
			justify-content: center;
			align-items: center;
			margin-top: 20px;
			img {
				width: 344px;
				height: 110px;
			}
			span {
				font-family: PingFangSC, PingFang SC;
				font-weight: 600;
				font-size: 24px;
				color: #FFFFFF;
				line-height: 33px;
				text-shadow: 0px 2px 0px #2276C8;
				text-align: left;
				font-style: normal;
			}
		}
		.item:nth-child(odd){
			span {
				position: absolute;
				left: 30px;
			}
		}
		.item:nth-child(even){
			span {
				position: absolute;
				right: 30px;
			}
		}
	}
}
</style>
