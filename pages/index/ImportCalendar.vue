<template>
	<view>
		<JCalendar 
		:yearMonth="targetDate" :dataSource="signData"
		 @dateChange="getData" @clickChange="clickSign"	 >
		 </JCalendar>
		 <!-- <view class="TipArea ">
			Tip:
			<p>打卡成功后需要你<text class="impTip">同步数据给数据库，切换月或重新进入</text>
			页面再向数据库读取记录(不会的建议参考我的Demo,而不是单独下个组件过来瞎折腾)。本地打卡不做任何记录，<text class="impTip">仅仅模拟成功</text>
			</p>
		 </view> -->
		<view class='count'>
			<text>截至目前，已坚持打卡</text>
			<view class='daynumber'>
				<text class='number'>{{sumCount}}</text>
				<text class='day'>天</text>
			</view>

			<view>本月累积打卡<text class="monthSum">{{signData.length}}</text>天</view>
			<text>请再接再厉，继续努力!</text>
		</view>
	</view>
</template>

<script>
	import JCalendar from '@/components/j-calendar.vue';

	export default {
		data() {
			return {
				targetDate: parseInt(new Date().getFullYear())+"-"+parseInt(new Date().getMonth() + 1), //本月
				sumCount: 0,
				signData: []
			};
		},
		components: {
			JCalendar
		},
		created() {
			//获取当前用户当前任务的签到状态
			this.getData(this.targetDate);
		},
		methods: {
			clickSign(day) {
				this.signData.push(day);
				this.sumCount++
				//this.$http.postHttp("Comment/UpdateRecord", day, (res) => {//可以通过后台接口添加当前用户当日打卡记录，
				// 		//console.log(res);
				// 		//if (res!= undefined) {
				// 			uni.showToast({
				// 				title: "打卡成功"+day,
				// 				icon: 'success',
				// 				duration: 2000
				// 			});
				// 		
				// 		//}
				//  })	
			},
			//当模板的时候可以直接引入，然后触发子组件事件到父界面去控制数据

			//获取当前用户该任务的签到数组
			getData(yearAndMonth) {
				let y=yearAndMonth.split('-')[0];
				let m=yearAndMonth.split('-')[1];
				//this.$http.postHttp("Comment/GetRecord", {//可以通过后台接口去获取你的打卡数据
				// 	Year: y,
				// 	Month: m,
				// }, (res) => {
				this.sumCount = 88; //res.SumCount
				
				if(yearAndMonth===this.targetDate){
					//这是我造的假数据！！！
					const num=["1","04","7","13","14","15"],
					newSign = [],
					today = new Date().getDate();
					for(let i=0;i<6;i++){
						if(parseInt(num[i])>today){ // 过滤掉今天之后的日子
							break;
						}
						newSign.push(this.targetDate+"-"+num[i])
					}
					// console.log(newSign);//-------------最后传给组件的格式看这里
					this.signData = newSign;
				}else{
					this.signData = [];
				}
	
				// })
			},
		}
	}
</script>

<style>
	.count .daynumber {
		display: flex;
		flex-direction: row;
		justify-content: center;
	}

	.count .daynumber .day {
		margin-top: 50rpx;
	}

	.count {
		margin: 20rpx;
		padding: 30rpx;
		display: flex;
		text-align: center;
		border-radius: 10px;
		flex-direction: column;
		justify-content: center;
		background-color: #fff;
		align-items: center;
	}

	.count .number {
		color: #fff;
		font-size: 60rpx;
		background-color: #94db98;
		width: 100rpx;
		height: 100rpx;
		border-radius: 50%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		margin: 20rpx;
	}

	.monthSum {
		color: red;
		font-size: 40rpx;
	}

	.count text {
		margin: 10rpx;
	}
	
	.TipArea{
		word-break:break-all;
		word-wrap:break-word;
		
		font-size: 14px;
		padding: 10px;
	}
	.impTip{
		display: inline-block;
		color: #ff0000;
	}
</style>
