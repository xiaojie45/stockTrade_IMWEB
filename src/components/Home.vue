<template>
	<div>
		<h4>当前你有:{{funds | currency}}</h4>
		<h4>点击“结束当天交易”即可开启新的交易日</h4>
	</div>
</template>
<script>
	export default {
		computed:{
			funds(){
				return this.$store.getters.funds
			}
		}
	}
</script>
<style>
	
</style>