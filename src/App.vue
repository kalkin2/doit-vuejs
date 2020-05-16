<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput v-on:addTodoparent="addTodo1"></TodoInput>
    <TodoList v-on:removeTodoParent="removeItem" v-bind:propsTodoItems="todoItems"></TodoList>
    <TodoFooter v-on:deleteAllPlease="deleteAllItems"></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader'
import TodoInput from './components/TodoInput'
import TodoList from './components/TodoList'
import TodoFooter from './components/TotoFooter'

export default {
  data() {
    return {
      todoItems: []
    }
  }
  ,methods: {
    addTodo1(todoItem) {
      localStorage.setItem(todoItem, todoItem)
      this.todoItems.push(todoItem)
    },
    deleteAllItems() {
      console.log('App.vue===> deleteAllItems');
      this.todoItems = [];
    },removeItem(index) {
      this.todoItems.splice(index,1)
    }

  },
  components: {
    'TodoHeader': TodoHeader,
    'TodoInput': TodoInput,
    'TodoList': TodoList,
    'TodoFooter': TodoFooter
  }
  ,created(){
    if(localStorage.length >0){
      for(var i=0; i < localStorage.length; i++){
        this.todoItems.push(localStorage.key(i));
      }
    }
  },

}
</script>

<style>
body {
  text-align: center;
  background-color: #F6F6F6;
}
input {
  border-style: groove;
  width: 200px
}
button {
  border-style: groove;
}
.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>
