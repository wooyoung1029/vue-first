<template>
	<view>
		<Header1 :header="header" ref="header" />
		子组件传来 {{runTime}}
	</view>
</template>

<script>
	import Header1 from "./header.1.vue"
	export default {
		components: {Header1},
		name: 'Test',
		data() {
			return {
				header: "父级组件传入Header组件",
				runTime: ""
			}
		},
		mounted() {
			this.$refs.header.num = 222
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
