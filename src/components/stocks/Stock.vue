<template>
	<div class="col-sm-6 col-md-4">
		<div class="panel panel-success">
			<div class="panel-heading">
				<h3 class="panel-title">{{stock.name}}  <small>(当前价格:{{stock.price}})</small></h3>
			</div>
			<div class="panel-body">
				<div class="pull-left">
					<input type="number"  class="form-control" placeholder="数量" v-model="quantity">
				</div>
				<div class="pull-right">
				<button class="btn btn-success" @click="buyStock"
				:disabled = "insufficient || quantity <= 0 || !Number.isInteger(+quantity)"
				>{{insufficient ? "资金不足" : "购买" }}</button></div>
			</div>
		</div>
	</div>
</template>
<script>
	export default {
		data(){
			return {
				quantity:0
			}
		},
		props:['stock'],
		computed:{
			funds(){
				return this.$store.getters.funds
			},
			insufficient(){
				return this.quantity * this.stock.price > this.funds;
			}
		},
		methods: {
			buyStock(){
				const order ={
					stockId:this.stock.id,
					stockQuantity:+this.quantity,
					stockPrice:this.stock.price
				};
				console.log(order)
				this.$store.dispatch('buyStock',order)
				this.quantity = 0;
			}
		}
	}
</script>
<style>
	.pull-left {
		width: 65%;
	}
</style>