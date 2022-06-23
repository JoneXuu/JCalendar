<template>
	<view class="content">
		<image class="logo" src="/static/Aes.jpg"></image>
		<!-- <view class="text-area">
			<navigator url="../../components/j-calendar" class="title">直接去模板页面</navigator>
		</view> -->
		<view class="text-area ">
			<navigator url="./ImportCalendar" class="title">去打卡</navigator>
		</view>	
		<view class="text-area ">
			<text>喜欢请点赞、给我一丝前进的动力</text>
		</view>		
		<view class="text-area ">
			<text>Thanks for your appreciation. </text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: ''
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {		
		width: 500upx;
		height: 300upx;
		margin-top: 200upx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50upx;
	}
	.text-area {
		margin: 10px 0;
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36upx;
		color: #8f8f94;
	}
</style>
