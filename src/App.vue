<template>
	<div id="app">
		<div class="wrapper">
			<header>My personal costs </header>
			<main>
				<add-payment-form @addNewPayment="onDataPaymentAdd" />
				<payments-display :items="paymentsList" />
				
			</main>
		</div>

	</div>
</template>

<script>
import PaymentsDisplay from './components/PaymentsDisplay.vue';
import AddPaymentForm from './components/AddPaymentForm.vue';

export default {
	name: 'App',
	data() {
		return {
			paymentsList: []
		}
	},
	components: {
		PaymentsDisplay,
		AddPaymentForm
	},
	methods: {
		fetchData (){
			return [
				
				{
					date:'28.03.2022',
					category:'Transport',
					value: 360
				},
				{
					date:'02.04.2022',
					category:'Food',
					value: 169
				},
				{
					date:'03.04.2022',
					category:'Transport',
					value: 532
				}
			]
		},
		onDataPaymentAdd(data){
			this.paymentsList.push(data)
		}
	},
	created() {
		this.paymentsList = this.fetchData()
	},
	
}
</script>

<style lang="scss" scoped>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
	text-align: left;
}
 header {
	font-size: 25px;
	font-weight: 800;
	margin-bottom: 25px;
 }


</style>
