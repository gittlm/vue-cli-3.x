<template>
  <div id="app">
    <Header :addName="addName"></Header>
    <List :items="items" :delName="delName"></List>
    <Footer :items="items"
      :checkAllName="checkAllName"
      :delChecked="delChecked"></Footer>
  </div>
</template>

<script>
import Header from './pages/Header.vue'
import Footer from './pages/Footer.vue'
import List from './pages/List.vue'

export default {
  name: 'App',
  components: {
    Header,
    Footer,
    List
  },
  data(){
    return {
      items:[
        {
          name:"吃饭",
          done:true
        },
        {
          name:"睡觉",
          done:false
        },
        {
          name:"打豆豆",
          done:false
        }
      ]
    }
  },
  methods:{
    addName:function(obj){
      this.items.unshift(obj)
    },
    delName:function(index){
      this.items.splice(index,1)
    },
    checkAllName:function(value){
      this.items.forEach(function(item){
        item.done = value
      })
    },
    delChecked:function(){
      this.items = this.items.filter(function(item){
        //这个过滤一直想不明白
        return !item.done
      })
    }
  }
}
</script>

<style scoped>
#app{
  width: 600px;
  margin: 100px auto;
}
</style>
