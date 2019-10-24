<template>
  <div>
    <h2>Менеджер задач</h2>
    <router-link to="/" class="home"></router-link>
    <AddTodo 
      @add-todo="addTodo"
    />
    <select v-model="filter">
      <option value="all">Все</option>
      <option value="completed">Выполненные</option>
      <option value="not-completed">Не выполненные</option>
    </select>
    <Loader v-if="loading" />
    <TodoList
      v-else-if="filteredTodos.length"
      v-bind:todos="filteredTodos"
      @remove-todo="removeTodo"
    />
    <p v-else>Задач нет</p>
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import AddTodo from '@/components/AddTodo'
import Loader from '@/components/Loader'
export default {
  name: 'app',
  data(){
    return {
      todos: [],
      loading: true,
      filter: 'all'
    }
  },
  mounted(){
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
      .then(response => response.json())
      .then(json => {
        setTimeout(() => {
          this.todos = json
          this.loading = false
        }, 1000)
        
      })
  },
  computed: {
    filteredTodos(){
      if (this.filter === 'all'){
        return this.todos
      }
      if (this.filter === 'completed'){
        return this.todos.filter(t => t.completed)
      }
      if (this.filter === 'not-completed'){
        return this.todos.filter(t => !t.completed)
      }
    }
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
    TodoList, AddTodo, Loader
  }
}
</script>

<style scoped>
  h2{
    color: #224B7A;
    font-size: 30px;
  }
  .home{
    position: absolute;
    top: 20px;
    left: 20px;
    background-image: url("../assets/home.png");
    background-size: cover;
    width: 50px;
    height: 50px;
    border: 3px solid #4A76A8;
    border-radius: 5px;
  }
  .home:hover{
    transform: rotate(360deg);
    transition: 2s;
  }
  select{
    margin: 20px;
    width: 200px;
    height: 30px;
  }
</style>