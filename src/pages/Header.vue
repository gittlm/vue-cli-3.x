<template>
	<div id="Header">
		<h1>Todo List</h1>
		<input 
			type="text" 
			v-model.trim="value"
			@keyup.enter="addItem()">
	</div>
</template>

<script>
	export default {
		name:"Header",
		props:{
			addName:Function
		},
		data(){
			return {
				value:''
			}
		},
		methods:{
			addItem(){
				var name = this.value
				if(!name){
					alert("请输入内容！")
					return
				}else{
					var obj={
						"name":name,
						"done":false
					}
					this.addName(obj)
					this.value = ''
				}
				
			}
		}
	}
</script>

<style scoped>
#Header{
	width: 100%;
}
h1{
	text-align: center;
	width: 100%;
}
input{
	width: 100%;
	line-height: 35px;
	height: 35px;
	padding: 0 10px;
}
</style>