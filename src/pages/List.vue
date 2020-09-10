<template>
	<div id="List">
		<Item v-for="(item,index) in items"
			:key="index"
			:item="item"
			:index="index"
			:delName="delName"></Item>
	</div>
</template>

<script>
	import Item from './Item.vue'
	export default {
		name:"List",
		props:{
			items:Array,
			delName:Function
		},
		components:{
			Item
		}
	}
</script>

<style scoped>
	
</style>