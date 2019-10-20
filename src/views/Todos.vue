<template>
  <div>
    <h2>Менеджер задач</h2>
    <router-link to="/">Home</router-link>
    <AddTodo 
      @add-todo="addTodo"
    />
    <hr>
    <TodoList 
      v-bind:todos="todos"
      @remove-todo="removeTodo"
    />
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import AddTodo from '@/components/AddTodo'
export default {
  name: 'app',
  data(){
    return {
      todos: []
    }
  },
  mounted(){
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(response => response.json())
      .then(json => {
        this.todos = json
      })
  },
  methods: {
    removeTodo(id){
      this.todos = this.todos.filter(t => t.id !== id)
    },
    addTodo(todo){
      this.todos.push(todo)
    }
  },
  components: {
    TodoList, AddTodo
  }
}
</script>