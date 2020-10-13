<template>
	<view class="container">
		<view class="intro">页面跳转</view>
		<text class="intro">详见：</text>
	</view>
</template>

<script>
	export default {
		onLoad: function(option) { //option为object类型，会序列化上个页面传递的参数
			console.log(JSON.parse(decodeURIComponent(option.param))); //打印出上个页面传递的参数。
		},
		data() {
			return {
				href: 'https://uniapp.dcloud.io/component/README?id=uniui',
				iconClassList: [{
					"name": "arrowdown",
					"unicode": "e581"
				}, {
					"name": "arrowleft",
					"unicode": "e582"
				}, {
					"name": "arrowright",
					"unicode": "e583"
				}, {
					"name": "arrowup",
					"unicode": "e580"
				}, {
					"name": "arrowthindown",
					"unicode": "e585"
				}],
				activeIndex: -1,
				checked: false
			}
		},
		methods: {
			change(e) {
				// e.detail.value在安卓手机上可能是String类型，后续修复后要修改
				this.checked = e.detail.value === 'false' || !e.detail.value ? false : true
			},
			switchActive(index) {
				this.activeIndex = index
			}
		}
	}
</script>

<style>
	.container {
		padding: 20px;
		font-size: 14px;
		line-height: 24px;
	}

	@charset "UTF-8";

	/* 头条小程序组件内不能引入字体 */
	/* #ifdef MP-TOUTIAO */
	@font-face {
		font-family: uniicons;
		font-weight: normal;
		font-style: normal;
		src: url("~@/static/uni.ttf") format("truetype");
	}

	/* #endif */
	/* #ifndef APP-NVUE */
	page {
		display: flex;
		flex-direction: column;
		box-sizing: border-box;
		background-color: #efeff4;
		min-height: 100%;
		height: auto;
	}

	view {
		font-size: 14px;
		line-height: inherit;
	}

	.example {
		padding: 0 15px 15px;
	}

	.example-info {
		padding: 15px;
		color: #3b4144;
		background: #ffffff;
	}

	.example-body {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: center;
		padding: 0;
		font-size: 14px;
		background-color: #ffffff;
	}

	/* #endif */
	.example {
		padding: 0 15px;
	}

	.example-info {
		/* #ifndef APP-NVUE */
		display: block;
		/* #endif */
		padding: 15px;
		color: #3b4144;
		background-color: #ffffff;
		font-size: 14px;
		line-height: 20px;
	}

	.example-info-text {
		font-size: 14px;
		line-height: 20px;
		color: #3b4144;
	}

	.example-body {
		flex-direction: column;
		padding: 15px;
		background-color: #ffffff;
	}

	.word-btn-white {
		font-size: 18px;
		color: #FFFFFF;
	}

	.word-btn {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: row;
		align-items: center;
		justify-content: center;
		border-radius: 6px;
		height: 48px;
		margin: 15px;
		background-color: #007AFF;
	}

	.word-btn--hover {
		background-color: #4ca2ff;
	}

	.example-body {
		padding: 0;
		flex-direction: row;
		flex-wrap: wrap;
	}

	.uni-right {
		flex-direction: row;
		flex-wrap: nowrap;
		align-items: center;
		color: #666;
	}

	.uni-right-text {
		font-size: 28rpx;
	}

	.switch {
		transform: scale(0.8);
		margin-left: 5px;
	}

	.icon-item {
		/* #ifndef APP-NVUE */
		display: flex;
		box-sizing: border-box;
		/* #endif */
		width: 135rpx;
		padding: 30rpx 10rpx;
		text-align: center;
		flex-direction: column;
	}

	.icon-item-text {
		font-size: 24rpx;
		text-align: center;
		overflow: hidden;
		text-overflow: ellipsis;
		white-space: nowrap;
	}
</style>
