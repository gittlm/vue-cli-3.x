<template>
	<div id="Footer">
		<input type="checkbox" v-model="checkAll">
		<span>{{checked}}/{{total}}</span>
		<button @click="delCheck">删除选中</button>
	</div>
</template>

<script>
	export default {
		name:"Footer",
		props:{
			items:Array,
			checkAllName:Function,
			delChecked:Function,
		},
		computed:{
			total(){
				return this.items.length
			},
			checked(){
				return this.items.reduce(function(checked,item){
					if(item.done){
						checked = checked + 1
					}
					return checked
				},0)
			},
			checkAll:{
				get(){
					return (this.total == this.checked) && this.total!=0
				},
				set(value){
					this.checkAllName(value)
				}
			}
		},
		methods:{
			delCheck:function(){
				if(window.confirm("是否确认删除已选中的项目?")){
					this.delChecked()
				}
			}
		}
	}
</script>

<style scoped>
	#Footer{
		width: 100%;
		height: 35px;
		line-height: 35px;
		padding: 0 10px;
	}
	button{
		float: right;
		margin-top: 6px;
	}
</style>