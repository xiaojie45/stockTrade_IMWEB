<template>
	<div class="col-sm-6 col-md-4">
		<div class="panel panel-info">
			<div class="panel-heading">
				<h3 class="panel-title">{{stock.name}}  <small>(当前价格:{{stock.price}} | 数量：{{stock.quantity}})</small></h3>
			</div>
			<div class="panel-body">
				<div class="pull-left">
					<input type="number"  class="form-control" placeholder="数量" v-model="quantity">
				</div>
				<div class="pull-right">
				<button class="btn btn-success" @click="sellStock"
				:disabled = "insufficient || quantity <= 0 || !Number.isInteger(+quantity)"
				>{{insufficient ? "数量不足":"出售"}}</button></div>
			</div>
		</div>
	</div>
</template>
<script>
	import {mapActions} from 'vuex';
	export default {
		data(){
			return {
				quantity:0
			}
		},
		computed:{
			insufficient(){
				return this.quantity > this.stock.quantity
			}
		},
		props:['stock'],
		methods: {
			...mapActions({
				sellOrder:"sellStock"
			}),
			sellStock(){
				const order ={
					stockId:this.stock.id,
					stockPrice:this.stock.price,
					stockQuantity:+this.quantity
				};
				this.sellOrder(order);
				this.quantity = 0;
			}
		}
	}
</script>
<style>
	
</style>