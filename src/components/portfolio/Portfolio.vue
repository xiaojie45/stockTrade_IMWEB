<template>
	<div>
		<app-stock v-for="stock in stocks" :stock='stock'></app-stock>
	</div>
</template>
<script>
	import {mapGetters} from 'vuex'
	import stock from './Stock.vue'
	export default {
		computed:{
			...mapGetters({
				stocks:'stocksPortfolio'
			})
		},
		components:{
			appStock:stock

		}
	}
</script>
<style>
	
</style>