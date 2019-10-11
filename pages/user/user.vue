<template>
	<view class="content">
		<view class="user-img">
			<image src="../../static/img/user.png" mode="" class="user-img-img"></image>
			<view class="username">
				<text>{{user}}</text>
			</view>

		</view>
		<view class="">
			<uni-collapse @change="change" accordion="true">
				<uni-collapse-item title="用户信息" :show-animation="true">
					<view style="padding: 30upx;">
						<text>用户信息</text>
					</view>
				</uni-collapse-item>
				<uni-collapse-item title="联系我们" :show-animation="true">
					<view style="padding: 30upx;">
						<text>联系我们</text>
					</view>
				</uni-collapse-item>
			</uni-collapse>
		</view>
		<view class="btn-row">
			<button v-if="!hasLogin" type="primary" class="primary" @tap="bindLogin">登录</button>
			<button v-if="hasLogin" type="default" @tap="bindLogout">退出登录</button>
		</view>
	</view>
</template>

<script>
	import uniCollapse from "@/components/uni-collapse/uni-collapse.vue"
	import uniCollapseItem from "@/components/uni-collapse-item/uni-collapse-item.vue"
	import {
		mapState,
		mapMutations
	} from 'vuex'

	export default {
		components: {
			uniCollapse,
			uniCollapseItem
		},
		data() {
			return {
				user: ''
			}
		},
		computed: {
			...mapState(['hasLogin', 'forcedLogin', 'userName'])
		},
		onLoad() {
			this.user = this.userName;
		},
		methods: {
			...mapMutations(['logout']),
			bindLogin() {
				uni.navigateTo({
					url: '../login/login',
				});
			},
			bindLogout() {
				this.logout();
				/**
				 * 如果需要强制登录跳转回登录页面
				 */
				if (this.forcedLogin) {
					uni.reLaunch({
						url: '../login/login',
					});
				}
			},
			change(e) {
				console.log(e)
			}
		}
	}
</script>

<style scoped>
	.user-img {
		height: 150px;
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
	}

	.username {
		margin-top: 10px;
	}

	.user-img-img {
		width: 40px;
		height: 40px;
	}
</style>
