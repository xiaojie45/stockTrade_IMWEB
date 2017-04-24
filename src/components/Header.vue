<template>
	<div>
	<nav class="navbar navbar-default" role="navigation">
		<div class="container-fluid">
			<div class="navbar-header">
				<router-link to="/" class="navbar-brand">首页</router-link>
			</div>
			<div class="collapse navbar-collapse">
	      		<ul class="nav navbar-nav">
	      			<router-link to="/portfolio" tag='li' activeClass='active'><a>个人中心</a></router-link>
	      			<router-link to="/stocks" tag='li' activeClass='active'><a>股票市场</a></router-link>
	      		</ul>
	      		<strong class="navbar-right navbar-text">
	      			资金：{{funds | currency}}
	      		</strong>
	      		 <ul class="nav navbar-nav navbar-right">
			        <li><a href="#" @click="endDay">结束当天交易</a></li>
			        <!-- <li class="dropdown">
			          <a href="#" class="dropdown-toggle" data-toggle="dropdown" role="button" aria-haspopup="true" aria-expanded="false">保存/加载 <span class="caret"></span></a>
			          <ul class="dropdown-menu">
			            <li><a href="#">保存</a></li>
			            <li><a href="#">加载</a></li>
			          </ul>
			        </li> -->
			      </ul>
	      	</div>
		</div>
	</nav>
	</div>
</template>
<script>
	import {mapActions} from 'vuex'
	export default {
		computed:{
			funds(){
				return this.$store.getters.funds
			}
		},
		methods:{
			...mapActions([
				'randomizeStocks'
				]),
			endDay(){
				this.randomizeStocks();

			}
		}
	}
</script>
<style>
	
</style>