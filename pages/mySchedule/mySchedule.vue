<template>
	<view class="content">
		<view class="status_bar">

		</view>
		<view class="status_bar_content">连为报修平台<view class="edit" @click="toEdit">
				<image src="../../static/img/edit.png" mode="" class="icon-edit"></image>
			</view>
		</view>
		<reserve-date @changeDay='changeDay' />
	</view>
</template>

<script>
	import {
		mapState
	} from 'vuex'

	import reserveDate from "@/components/reserve-date/reserve-date.vue"
	export default {
		components: {
			reserveDate
		},
		computed: mapState(['forcedLogin', 'hasLogin', 'userName']),
		data() {
			return {
				priceList: []
			}
		},
		onLoad() {
			if (!this.hasLogin) {
				uni.showModal({
					title: '未登录',
					content: '您未登录，需要登录后才能继续',
					/**
					 * 如果需要强制登录，不显示取消按钮
					 */
					showCancel: !this.forcedLogin,
					success: (res) => {
						if (res.confirm) {
							/**
							 * 如果需要强制登录，使用reLaunch方式
							 */
							if (this.forcedLogin) {
								uni.reLaunch({
									url: '../login/login'
								});
							} else {
								uni.navigateTo({
									url: '../login/login'
								});
							}
						}
					}
				});
			}
		},
		methods: {
			changeDay(data) {
				console.log(data)
			},
			toEdit() {
				uni.navigateTo({
					url: './scheduleEdit',
					animationType: 'pop-in',
					animationDuration: 200
				});
			}
		}
	}
</script>

<style>
	.content {

		padding: 0;
	}

	.edit {
		z-index: 999;
		position: absolute;
		right: 10px;
		top: 7px;
	}

	.icon-edit {
		height: 30px;
		width: 30px;
	}
</style>
