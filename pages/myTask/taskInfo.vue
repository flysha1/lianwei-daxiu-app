<template>
	<view class="content">
		<view class="status_bar">

		</view>
		<view class="status_bar_content">
			<text>{{id}}</text>
			<uni-icon type="back" size="30" class="icon-back" @click="back"></uni-icon>
		</view>
		<view class="">
			<view class="tab-title">
				<view :class="tabClass1" @click="onClickItem(0)">
					<text>处理</text>
				</view>
				<view :class="tabClass2" @click="onClickItem(1)">
					<text>详情</text>
				</view>
			</view>
			<view class="tab-content">
				<view v-if="current === 0">
					
					<view class="form-title">
						<text>新的报修单</text>
					</view>
					<view class="form-item">
						<view class="form-label"><text>报修时间</text></view>
						<view class="form-content">
							<text>{{formData.date}}</text>
						</view>
					</view>
					<view class="form-item">
						<view class="form-label"><text>公司</text></view>
						<view class="form-content">
							<text>{{formData.company}}</text>
						</view>
					</view>
					<view class="form-item">
						<view class="form-label"><text>门店</text></view>
						<view class="form-content">
							<text>{{formData.store}}</text>
						</view>
					</view>
					<view class="form-item">
						<view class="form-label"><text>响应等级</text></view>
						<view class="form-content">
							<text>{{formData.level}}</text>
						</view>
					</view>
					<view class="form-item">
						<view class="form-label"><text>是否加急</text></view>
						<view class="form-content">
							<text>{{formData.level}}</text>
						</view>
					</view>
					<view class="form-item">
						<view class="form-label"><text>报修类型</text></view>
						<view class="form-content">
							<text>{{formData.type}}</text>
						</view>
					</view>
					<view class="form-item">
						<view class="form-label"><text>位置</text></view>
						<view class="form-content">
							<text>{{formData.location}}</text>
						</view>
					</view>
					<view class="form-item">
						<view class="form-label"><text>保险项目</text></view>
						<view class="form-content">
							<text>{{formData.matter}}</text>
						</view>
					</view>
					<view class="btn">
						<button type="primary" class="btn-option">接单</button>
						<button class="btn-option btn-refuse" hover-class="btn-refuse-hover">驳回</button>
					</view>
				</view>
				<view v-else>
					<uni-collapse @change="change">
						<uni-collapse-item title="报修状态" :show-animation="true">
							<view style="padding: 30upx;">
								<text>报修状态</text>
							</view>
						</uni-collapse-item>
						<uni-collapse-item title="门店信息" :show-animation="true">
							<view style="padding: 30upx;">
								<text>门店信息</text>
							</view>
						</uni-collapse-item>
						<uni-collapse-item title="报修信息" :show-animation="true">
							<view style="padding: 30upx;">
								<text>门店信息</text>
							</view>
						</uni-collapse-item>
						<uni-collapse-item title="维修方案" :show-animation="true">
							<view style="padding: 30upx;">
								<text>门店信息</text>
							</view>
						</uni-collapse-item>
						<uni-collapse-item title="材料和人工" :show-animation="true">
							<view style="padding: 30upx;">
								<text>门店信息</text>
							</view>
						</uni-collapse-item>
						<uni-collapse-item title="时间安排" :show-animation="true">
							<view style="padding: 30upx;">
								<text>门店信息</text>
							</view>
						</uni-collapse-item>
						<uni-collapse-item title="反馈" :show-animation="true">
							<view style="padding: 30upx;">
								<text>门店信息</text>
							</view>
						</uni-collapse-item>
						<uni-collapse-item title="附件" :show-animation="true">
							<view style="padding: 30upx;">
								<text>门店信息</text>
							</view>
						</uni-collapse-item>
					</uni-collapse>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import uniCollapse from "@/components/uni-collapse/uni-collapse.vue"
	import uniCollapseItem from "@/components/uni-collapse-item/uni-collapse-item.vue"
	import uniIcon from "@/components/uni-icon/uni-icon.vue"
	export default {
		components: {
			uniIcon,
			uniCollapse,
			uniCollapseItem
		},
		data() {
			return {
				tabClass1: 'tab-title-item tab-title-item-active',
				tabClass2: 'tab-title-item',
				current: 0,
				items: ['处理', '详情'],
				id: '',
				formData: {
					id: 'R028011709',
					isUrgent: true,
					type: '空调',
					date: '2019-08-12',
					matter: '空调内机',
					segment: '等待区域经理接单',
					company: '迪士尼英语培训学校',
					store: '南京二号-NJDB',
					level: 'P2',
					location: '教室'
				}
			}
		},
		onLoad(option) {
			this.id = option.id
			console.log(option.id);
		},
		methods: {
			back() {
				uni.navigateBack({
					delta: 1,
					animationType: 'pop-out',
					animationDuration: 200
				});
			},
			onClickItem(e) {
				console.log(e)
				this.current = e
				let a = ''
				a = this.tabClass2
				this.tabClass2 = this.tabClass1
				this.tabClass1 = a
			},
			change(e) {
				console.log(e)
			}
		}
	}
</script>

<style scoped>
	.icon-back {
		position: absolute;
		z-index: 999;
		left: 10px;
		bottom: 0px;
	}

	.tab-title {
		margin-top: 10px;
		margin-bottom: 5px;
		display: flex;
	}

	.tab-title-item {
		width: 80px;
		text-align: center;
		padding: 5px 0px;
		margin: 0 10px;
	}

	.tab-title-item-active {
		border-bottom: 2px solid rgb(15, 174, 255);
		color: rgb(15, 174, 255);
	}

	.tab-content {
		background-color: #fff;
		min-height: 84vh;
	}

	.form-title {
		text-align: center;
		padding: 10px;
		margin: 0 5px;
		font-size: 20px;
		border-bottom: 0.5px solid #555;
	}

	.btn {
		padding: 0 10px;
	}

	.btn-option {
		color: #fff;
		margin-top: 10px;
	}

	.btn-refuse {
		background-color: #ffc700;
	}

	.btn-refuse-hover {
		background-color: #d6b646
	}
</style>
