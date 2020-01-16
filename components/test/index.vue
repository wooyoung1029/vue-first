<template>
	<view>
		<Header :header="header" ref="header"></header>
	</view>
</template>

<script>
	import Header from "./header.vue"
	export default {
		components: {Header},
		name: 'Test1',
		data() {
			return {
				header: "父级组件传入Header组件"
			}
		},
		mounted() {
			// this.$refs.header.num = 222
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
