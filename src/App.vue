<template>
<div class="flex items-center justify-center bg-gray-200 h-screen">
<div>
  <AddTodo v-on:add-todo="getTodo" />
  <TodoList v-bind:todos="todos" v-on:remove-todo="removeTodo" /> 
</div>
</div>
</template>

<script>
import AddTodo from './components/AddTodo.vue';
import TodoList from './components/TodoList.vue';
export default {
  name: 'App',
  components: {
    AddTodo,
    TodoList
  },
  methods: {
    getTodo(todo){
      this.todos = [...this.todos, todo];
    },
    removeTodo(id){
      console.log(id, 'parent');
      this.todos = this.todos.filter(item=>item.id !==id);
    }
  },
  data: function(){
    return {
      todos: []
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
