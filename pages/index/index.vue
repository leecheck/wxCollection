<template>
	<view class="container">
		<view class="example-body">
			<view v-for="(item,index) in iconClassList" :key="index" class="icon-item" @click="switchActive(index)">
				<uni-icons :type="item.icon" :color="activeIndex === index?'#007aff':'#8f8f94'" size="25" />
				<text :style="{color:activeIndex === index?'#007aff':'#8f8f94'}" class="icon-item-text">{{ checked? item.icon: item.name }}</text>
			</view>
		</view>
		<uni-swiper-dot :info="info" :current="current" :mode="mode" :dots-styles="dotsStyles" field="content">
			<swiper class="swiper-box" @change="changeSwipe">
				<swiper-item v-for="(item, index) in info" :key="index">
					<view :class="item.colorClass" class="swiper-item">
						<image class="image" :src="item.url" mode="aspectFill" />
					</view>
				</swiper-item>
			</swiper>
		</uni-swiper-dot>
		<view class="title-line">
			<div>我的应用</div>
			<div @click="navi()">添加常用应用点我跳转</div>
		</view>
		<view class="example-body">
			<view v-for="(item,index) in iconClassList" :key="index" class="icon-item" @click="switchActive(index)">
				<uni-icons :type="item.icon" :color="activeIndex === index?'#007aff':'#8f8f94'" size="25" />
				<text :style="{color:activeIndex === index?'#007aff':'#8f8f94'}" class="icon-item-text">{{ checked? item.icon: item.name }}</text>
			</view>
		</view>
		<view class="example-body">
			<view v-for="(item,index) in iconClassList" :key="index" class="icon-item" @click="switchActive(index)">
				<uni-icons :type="item.icon" :color="activeIndex === index?'#007aff':'#8f8f94'" size="25" />
				<text :style="{color:activeIndex === index?'#007aff':'#8f8f94'}" class="icon-item-text">{{ checked? item.icon: item.name }}</text>
			</view>
		</view>
		<view class="title-line">
			<div>热门店铺</div>
			<div @click="navi()">更多</div>
		</view>
		<view class="card-view" >
			<view class="" style="width: 50%;">
				<uni-card :is-shadow="true" title="标题文字" mode="style" thumbnail="https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/shuijiao.jpg" @click="clickCard">
					<text class="content-box-text">餐饮</text>
					<text class="content-box-text">家有好面</text>
					<uni-rate :size="18" :value="5" />
				</uni-card>
			</view>
			<view class="" style="width: 50%;">
				<uni-card :is-shadow="true" title="标题文字" mode="style" thumbnail="https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/shuijiao.jpg" @click="clickCard">
					<text class="content-box-text">餐饮</text>
					<text class="content-box-text">家有好面</text>
					<uni-rate :size="18" :value="5" />
				</uni-card>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				href: 'https://uniapp.dcloud.io/component/README?id=uniui',
				iconClassList: [{
					"icon": "arrowdown",
					"name": "扫一扫",
					"unicode": "e581"
				}, {
					"icon": "arrowdown",
					"name": "会员码",
					"unicode": "e582"
				}, {
					"icon": "arrowdown",
					"name": "卡包",
					"unicode": "e583"
				}, {
					"icon": "arrowdown",
					"name": "停车缴费",
					"unicode": "e580"
				}, {
					"icon": "arrowdown",
					"name": "小票上传",
					"unicode": "e585"
				}],
				activeIndex: -1,
				checked: false,
				info: [{
						colorClass: 'uni-bg-red',
						url: 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/shuijiao.jpg',
						content: '内容 A'
					},
					{
						colorClass: 'uni-bg-green',
						url: 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/muwu.jpg',
						content: '内容 B'
					},
					{
						colorClass: 'uni-bg-blue',
						url: 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/cbd.jpg',
						content: '内容 C'
					}
				],
				modeIndex: -1,
				styleIndex: -1,
				current: 0,
				mode: 'default',
				dotsStyles: {
					backgroundColor: 'rgba(83, 200, 249,0.3)',
					border: '1px rgba(83, 200, 249,0.3) solid',
					color: '#fff',
					selectedBackgroundColor: 'rgba(83, 200, 249,0.9)',
					selectedBorder: '1px rgba(83, 200, 249,0.9) solid'
				}
			}
		},
		methods: {
			change(e) {
				// e.detail.value在安卓手机上可能是String类型，后续修复后要修改
				this.checked = e.detail.value === 'false' || !e.detail.value ? false : true
			},
			switchActive(index) {
				this.activeIndex = index
			},
			navi() {
				uni.navigateTo({
					url: '/pages/index/sub?param=' + encodeURIComponent(JSON.stringify({
						name: "name"
					})),
				});
			},
			clickCard() {
				uni.showToast({
					title: '点击卡片',
					icon: 'none'
				})
			},
			changeSwipe(e) {
				this.current = e.detail.current
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
	
	.card-view{
		display: flex;
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
