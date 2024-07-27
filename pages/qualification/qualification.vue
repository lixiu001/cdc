<template>
	<view>
		<div v-if="!hasPrizeQualification">
			<div>暂无领奖资格</div>
			<div>需要答对全部5道题才可去现场领奖哦</div>
		    <span @click="handleAction()">立即答题</span>
		</div>
		  <div v-if="hasPrizeQualification">
			  <div>恭喜你，你可凭此微信号到现场领取奖品。</div>
		      <span @click="handleAppointment()">立即预约</span>
		    </div>
	</view>
</template>

<script>
	import {post } from '../../utils/request.js'
	export default {
		data() {
			return {
				hasPrizeQualification: false
			};
		},
		created() {
		    this.fetchData();
		},
		methods: {
			fetchData() {
			 const params = {
				 "openId": "3333",
				}
		      post('/question/queryQuizRecord',params)
		        .then(response => {
		          this.hasPrizeQualification = response.data.quizCorrectQuantity === 5;
				  console.log(this.hasPrizeQualification)
		        })
		        .catch(error => {
		          console.error('API请求失败:', error);
		        });
		    }
			},
			handleAction() {
				console.log(111)
				uni.navigateTo({url: '/pages/answer/answer'})
			},
			handleAppointment() {
				// 替换成预约的地址
				uni.navigateTo({url: '/pages/answer/answer'})
			},
	}
</script>

<style lang="scss">

</style>
