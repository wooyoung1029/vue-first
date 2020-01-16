<template>
	<view>
		我是头部 {{header}} {{num}}
	</view>
</template>

<script>
	export default {
		name: 'Header',
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
		methods: {
			
		}
	}
</script>

<style>

</style>
