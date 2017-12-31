<template>
  <div id="app">
   <todo-list-input   v-on:add="addTask"></todo-list-input>
    <div v-if="todoLists.length">
      <ListShow   v-bind:TodoLists="todoLists" @deleteTask="deleteTask"></ListShow>
    </div>

  </div>
</template>

<script>
import TodoListInput from './components/TodoListInput'

import ListShow   from  './components/ListShow'

export default {
  name: 'app',
  components: {
    TodoListInput,
    ListShow
  },
  data(){
    return {
        todoLists:[]
    }
  },
  methods: {
    addTask:function (taskName,others) {
        if(this.todoLists.length){
            this.todoLists.push({"name":taskName,index:this.todoLists[this.todoLists.length-1].index+1});
        }else{
            this.todoLists.push({"name":taskName,index:0});
        }
      console.log(this.todoLists);

    },
    deleteTask:function (index) {
      this.todoLists=this.todoLists.filter(function (item) {
        if(item.index!==index){
            return true;
        }else {
            return false;
        }
      })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
