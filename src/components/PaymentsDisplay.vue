<template>
 <div class="payments-display-wrapper">
			<div class="item item__header">
				<p class="item__idx">#</p>
				<p class="item__date">Date</p>
				<p class="item__discription">Category</p> 
				<p class="item__value">Value</p>
			</div>
		<div class="item" v-for="(item, idx) in items" :key="idx">
			
			<p class="item__idx">{{ idx + 1}}</p>
			<p class="item__date">{{ item.date }}</p>
			<p class="item__discription">{{ item.category }}</p> 
			<p class="item__value">{{ item.value }}</p>
		</div>

 </div>


</template>

<script>

export default {
	name: "PaymentsDisplay",
	props:{
		items: {
				type: Array,
				default: () =>[],
		}
	},
};

</script>

<style lang="scss" scoped>
 .item {
	display: flex;
	border-bottom: 1px solid #ccc;
	max-width: 50%;	
	justify-content: space-between;
	.item__idx,
	.item__date,
	.item__discription,
	.item__value {
		width: 50px;
	}
 }
</style>