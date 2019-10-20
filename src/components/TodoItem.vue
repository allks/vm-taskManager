<template>
  <li>
    <span v-bind:class="{done: todo.completed}">
      <input type="checkbox" 
        v-on:change="todo.completed = !todo.completed">
      <strong>{{todo.id}}</strong>
      {{todo.title}}
    </span>
    <button class="rm"
      v-on:click="$emit('remove-todo', todo.id)"
    >&times;</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scroped>
  li{
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    padding: .5rem 2rem;
    margin-bottom: 1rem;
  }
  strong{
    margin: 0 1rem;
  }
  .rm{
    width: 30px;
    height: 30px;
    background-color: #ff2d00;
    color: #fff;
    border-radius: 50%;
    font-weight: bold;
    border: 0;
    cursor: pointer;
  }
  .rm:hover{
    background-color: #9d1c00;
  }
  .done{
    text-decoration: line-through;
  }
</style>