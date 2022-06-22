<template>
	<view>
		<view class="standView"></view>
		<u-navbar :is-Back="false" title="一键开团" :bgColor="bgColor">
		</u-navbar>
		<view> 一键开团 </view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				bgColor: '#f2fdff',
			}
		},
		methods: {

		}
	}
</script>

<style>
	.standView{
	  width: 100%;
	  height: 120rpx;     /*  此处高度需要修改 */
	  /* background-color: black; */
	}
</style>
