<template>
	<view>
		我是头部 {{header}} {{num}}
	</view>
</template>

<script>
	export default {
		name: 'Header1',
		props: {
			header: {
				type: String,
				default: ""
			}
		},
		data() {
			return {
				num: ""
			}
		},
		mounted() {
			this.$parent.runTime = new Date();
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
