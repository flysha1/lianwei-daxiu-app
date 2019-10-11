<template>
	<view class="content">
		<view class="status_bar">

		</view>
		<view class="status_bar_content">连为报修平台
		</view>
		<scroll-view class="lists" scroll-y="true">
			<view class="task-item" v-for="(i,index) in taskList" :key="index" @click="toTaskInfo(i)">
				<view class="task-item-top row">
					<view class="task-item-icon">
						<image src="../../static/img/isUrgent1.png" mode="" v-if="i.isUrgent" class="flag"></image>
						<image src="../../static/img/isUrgent0.png" mode="" v-else class="flag"></image>
					</view>
					<view class="task-item-main">
						<view class="row">
							<view class="label">
								<text>单号</text>
							</view>
							<view class="info">
								<text>{{i.id}}</text>
							</view>
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
								<text>报修时间</text>
							</view>
							<view class="info">
								<text>{{i.date}}</text>
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
						<view class="gutter">

						</view>
						<view class="row">
							<view class="label">
								<text>公司</text>
							</view>
							<view class="info">
								<text>{{i.company}}</text>
							</view>
						</view>
						<view class="row">
							<view class="label">
								<text>门店</text>
							</view>
							<view class="info">
								<text>{{i.store}}</text>
							</view>
						</view>
					</view>
				</view>
			</view>
		</scroll-view>

	</view>
</template>

<script>
	import uniCard from "@/components/uni-card/uni-card"
	export default {
		components: {
			uniCard
		},
		data() {
			return {
				taskList: [{
					id: 'R028011709',
					isUrgent: true,
					date: '2019-08-12',
					matter: '空调内机',
					segment: '等待区域经理接单',
					company: '迪士尼英语培训学校',
					store: '南京二号-NJDB'
				}, {
					id: 'R0KO011129',
					isUrgent: false,
					date: '2019-08-12',
					matter: '景观灯',
					segment: '提供维修方案',
					company: '迪士尼',
					store: '迪士尼陆家嘴旗舰店'
				}, {
					id: 'R0KO011129',
					isUrgent: false,
					date: '2019-08-12',
					matter: '景观灯',
					segment: '提供维修方案',
					company: '迪士尼',
					store: '迪士尼陆家嘴旗舰店'
				}]
			}
		},
		methods: {
			toTaskInfo(i) {
				uni.navigateTo({
					url: './taskInfo?id=' + i.id,
					animationType: 'pop-in',
					animationDuration: 200
				});
			}
		}
	}
</script>

<style scoped>
	.flag {
		width: 90upx;
		height: 90upx;
	}

	.lists {
		height: 90vh;
	}

	.task-item {
		background: #fff;
		margin-bottom: 10px;
	}

	.task-item-icon {
		width: 15%;
		margin: 10% 10px 0 10px;
	}

	.task-item-main {
		width: 85%;
	}

	.task-item-main .row {
		margin: 20upx 0;
	}

	.label {
		width: 35%;
	}

	.info {
		width: 65%;
	}

	.gutter {
		width: 100%;
		border-bottom: 2px solid #333333;
	}
</style>
