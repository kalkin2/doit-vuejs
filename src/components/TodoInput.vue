<template>
  <div  class="inputBox shadow ">
    <input type="text" v-model="newTodoItem" placeholder="type what you have to do " v-on:keyup.enter="addTodo">
   <span class="addContainer" v-on:click="addTodo">
      <i class="addBtn fa fa-plus" aria-hidden="true"></i>
    </span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodoItem: ''
    }
  },
  methods: {
    addTodo() {
      console.log('Todo input >> addTodo()');
      if(this.newTodoItem !==''){
      console.log(this.newTodoItem)
        var value = this.newTodoItem && this.newTodoItem.trim();
        this.$emit('addTodoparent',value)//value 값을 상위로 전달
      this.clearInput();
      }
    },
    clearInput() {
      this.newTodoItem = '';
    }
  }
}
</script>

<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  background: white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
}
.addContainer {
  float: right;
  background: linear-gradient(to right, #6478FB, #8763FB);
  display: inline-block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: white;
  vertical-align: middle;
}
</style>
