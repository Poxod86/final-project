<template>
	<div class="payment-content">
		<button class="payment-content__button" v-on:click="show = !show">{{ !show ? "ADD NEW COST +"  : 'HIDE'  }}</button>
		<div class="payment-content payment-content__form" v-if="show">
			<input placeholder="Payment description" v-model="category"/>
			<input placeholder="Payment amount" v-model.number="value"/>
			<input placeholder="Payment date" v-model="date"/>
			<button @click="onSaveClick">ADD <span>+</span></button>
		</div>
	</div>

</template>

<script>
export default {
	name: "AddPaymentForm",
	data() {
		return {
			date: '',
			category: '',
			value: 0,
			show: false
		}
	},
	computed: {
		getCurrentDate(){
			const today = new Date();
			const d = today.getDate();
			const m = today.getMonth() + 1;
			const y = today.getFullYear();
			return `${d}.${m}.${y}`
		}
	},
	methods: {
		onSaveClick(){
			const data = {
				date: this.date || this.getCurrentDate,
				category: this.category,
				value: this.value,
			}
			this.$emit('addNewPayment', data)
		},

	},
	
}


</script>

<style lang="scss" scoped>
.payment-content__button {
	background-color: #25a79a;
	color: #fff;
	width: 200px;
	padding: 7px;
	border: none;
	padding-left: 18px;
	text-align: left;
	margin-bottom: 10px;
	
}
.payment-content__form {
	display: flex;
	flex-direction: column;
	max-width: 50%;
	}

</style>