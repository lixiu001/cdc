<template>
	<view class="content">
		<div class="item" @click="jump(1)">
			<img src="/static/1.png" alt="" />
			<span>3D线上展厅</span>
		</div>
		<div class="item" @click="jump(2)">
			<img src="/static/2.png" alt="" />
			<span>预约展馆</span>
		</div>
		<div class="item" @click="jump(3)">
			<img src="/static/3.png" alt="" />
			<span>预约座椅</span>
		</div>
		<div class="item" @click="jump(4)">
			<img src="/static/4.png" alt="" />
			<span>答题领奖</span>
		</div>
	</view>
</template>

<script>
export default {
	data() {
		return {
			
		}
	},
	onLoad() {

	},
	methods: {
		jump(data){
			let pageMap = {
				1: '/pages/exhibition/exhibition',
				2: '/pages/reserveShowroom/reserveShowroom',
				3: '/pages/reserveSeat/reserveSeat',
				4: '/pages/question/question'
			}
			uni.navigateTo({url: pageMap[data]})
		}
	}
}
</script>

<style lang="scss" scoped>
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
</style>
