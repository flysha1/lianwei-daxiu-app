<template>
	<view class="cotent" style="width: 100%;">
		<form @submit="formSubmit">
			<view class="form-item">
				<view class="form-label"><text>区域</text></view>
				<view class="form-content">
					<input class="form-content-input" v-model="formData.area" disabled placeholder="请选择" @click="show(1)" />
				</view>
			</view>
			<view class="form-item">
				<view class="form-label"><text>报修类型</text></view>
				<view class="form-content">
					<input class="form-content-input" v-model="formData.type" disabled placeholder="请选择" @click="show(2)" />
				</view>
			</view>
			<view class="form-item">
				<view class="form-label"><text>报修项</text></view>
				<view class="form-content">
					<input class="form-content-input" v-model="formData.item" disabled placeholder="请选择" @click="show(3)" />
				</view>
			</view>
			<view class="form-item">
				<view class="form-label"><text>报修项</text></view>
				<view class="form-content">
					<text>P3</text>
				</view>
			</view>
			<view class="form-item">
				<view class="form-label"><text>是否加急</text></view>
				<view class="form-content">
					<switch :checked="formData.isUrgent" @change="switchChange" />
				</view>
			</view>
			<view class="form-item">
				<view class="form-label"><text>数量</text></view>
				<view class="form-content">
					<input class="form-content-input" v-model="formData.num" />
				</view>
			</view>
			<view class="form-item">
				<view class="form-label"><text>单位</text></view>
				<view class="form-content">
					<input class="form-content-input" v-model="formData.company" />
				</view>
			</view>
			<view class="form-item">
				<view class="form-label"><text>描述</text></view>
				<view class="form-content">
					<textarea maxlength="100" class="form-content-input textarea" v-model="formData.desc" />
					</view>
			</view>
			<view class="form-item">
				<view class="form-label"><text>附件</text></view>
				<view class="form-content others">
					<button type="default" class="btn-others" @click="getImg('camera')">拍照</button>
					<button type="default" class="btn-others" @click="getImg('album')">相册</button>
				</view>
			</view>
		</form>
		<view class="btn-submit">
			<button type="primary">提交</button>
		</view>
		<mpvue-city-picker ref="picker1" @onConfirm="onConfirm($event,'area')" themeColor="rgb(15, 174, 255)"></mpvue-city-picker>
		<mpvue-picker ref="picker2" mode="selector" :deepLength="1" themeColor="rgb(15, 174, 255)" @onConfirm="onConfirm($event,'type')"
		 :pickerValueArray="pickList.types"></mpvue-picker>
		<mpvue-picker ref="picker3" mode="selector" :deepLength="1" themeColor="rgb(15, 174, 255)" @onConfirm="onConfirm($event,'item')"
		 :pickerValueArray="pickList.items"></mpvue-picker>
	</view>
</template>

<script>
	import mpvuePicker from '@/components/mpvue-picker/mpvuePicker.vue';
	import mpvueCityPicker from '@/components/mpvue-citypicker/mpvueCityPicker.vue'
	import cityData from '@/common/city.data.js';
	import uniList from '@/components/uni-list/uni-list.vue'
	import uniListItem from '@/components/uni-list-item/uni-list-item.vue'
	export default {
		components: {
			uniList,
			uniListItem,
			mpvuePicker,
			mpvueCityPicker
		},
		data() {
			return {
				mode: '',
				pickerText: '',
				pickList: {
					types: [{
						label: '类型一',
						value: 1
					}, {
						label: '类型二',
						value: 2
					}, {
						label: '类型三',
						value: 3
					}],
					items: [{
						label: '项目一',
						value: 1
					}, {
						label: '项目二',
						value: 2
					}, {
						label: '项目三',
						value: 3
					}]
				},
				formData: {
					area: '',
					type: '',
					item: '',
					isUrgent: false,
					level: '',
					num: '',
					company: '',
					desc: '',
					img: {}
				}
			}
		},
		methods: {
			formSubmit(e) {
				console.log(e)
			},
			onConfirm(e, i) {
				this.formData[i] = e.label
			},
			show(i) {
				this.$refs['picker' + i].show()
			},
			switchChange(e) {
				this.formData.isUrgent = e.target.value
			},getImg(e){
				uni.chooseImage({
				    count: 1, //默认9
				    sizeType: ['original', 'compressed'], //可以指定是原图还是压缩图，默认二者都有
				    sourceType: [e],
				    success: function (res) {
				        console.log(JSON.stringify(res.tempFilePaths));
				    }
				});
				}
		}
	}
</script>

<style scoped>
	.form-content-input {
		width: 90%;
		font-size: 18px;
		line-height: 2em;
		height: 2em;
		min-height: 0;
		border: 0.5px solid #ccc;
		border-radius: 5px;
		padding-left: 10px;
	}
	.textarea{
		    height: 5em;
	}
	.btn-submit{
		margin-top: 10px;
		padding: 0 15px;
	}
	.btn-others{
		 width: 85px;
		 display: inline-block;
	}
</style>
