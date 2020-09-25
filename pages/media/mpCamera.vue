<template>
	<button type="default" @click="open">mpCamera</button>
</template>

<script>
	export default {
		methods: {
			open() {
				uni.createCameraContext({
						
				})
			}
		}
	}
</script>

<style>
</style>
