<template>
	<view class="content">
		<view class="status_bar">

		</view>
		<view class="status_bar_content">
			<view class="status_bar_content_main">
				<input type="text" v-model="val" placeholder="单号,状态,报修位置、类" class="search" />
				<uni-icon type="search" size="18" class="icon-search"></uni-icon>
			</view>
		</view>
		<view>
			<view class="item" v-for="(i,index) in lists" :key="index">
				<view class="item-date">
					<text>{{i.date}}</text>
				</view>
				<view class="row">
					<view class="label">
						<text>是否加急</text>
					</view>
					<view class="info">
						<text>{{i.isUrgent?'是':'否'}}</text>
					</view>
				</view>
				<view class="row">
					<view class="label">
						<text>报修单号</text>
					</view>
					<view class="info">
						<text>{{i.id}}</text>
					</view>
				</view>
				<view class="row">
					<view class="label">
						<text>报修项</text>
					</view>
					<view class="info">
						<text>{{i.matter}}</text>
					</view>
				</view>
				<view class="row">
					<view class="label">
						<text>流转环节</text>
					</view>
					<view class="info">
						<text>{{i.segment}}</text>
					</view>
				</view>
				<view class="row">
					<view class="label">
						<text>状态</text>
					</view>
					<view class="info">
						<text>{{i.status}}</text>
					</view>
				</view>
			</view>
		</view>
		<view class="more">
			<text>加载更多</text>
		</view>
	</view>
</template>

<script>
	import uniIcon from "@/components/uni-icon/uni-icon.vue"
	export default {
		components: {
			uniIcon
		},
		data() {
			return {
				val: '',
				lists: [{
					date: '2019-08-12',
					isUrgent: false,
					id: 'R028011709',
					matter: '',
					segment: '报修结束',
					status: '完成'
				}]
			}
		},
		methods: {

		}
	}
</script>

<style scoped>
	.status_bar_content {
		color: #333333;
	}

	.status_bar_content {
		display: flex;
		justify-content: center;
	}

	.status_bar_content_main {
		display: flex;
		padding: 5px;
		margin: 5px;
		background-color: #fff;
	}

	.search {
		text-align: left;
	}

	.icon-search {
		line-height: 22px;
	}

	.item {
		background-color: #fff;
		margin-top: 10px;
		padding: 5px 10px;
	}

	.row {
		margin: 10px 0;
	}

	.label {
		width: 30%;
	}

	.info {
		width: 70%;
	}

	.more {
		margin-top: 10px;
		text-align: center;
		font-weight: bold;
	}
</style>
