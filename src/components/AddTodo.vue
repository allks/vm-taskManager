<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="title">
    <button type="submit" class="cr">Создать</button>
  </form>
</template>

<script>
export default {
  data(){
    return{
      title: ''
    }
  },
  methods: {
    onSubmit(){
      if (this.title.trim()){
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false
        }
        this.$emit('add-todo', newTodo)
        this.title = ""
      }
    }
  }
}
</script>

<style scoped>
  form{
    display: flex;
    justify-content: center;
  }
  input{
    width: 400px;
    height: 30px;
    margin: 0 20px;
  }
  .cr{
    background-color: #4e73b5;
    color: #fff;
    border: 0;
    border-radius: 5px;
    cursor: pointer;

  }
  .cr:hover{
    background-color: #36507e;
  }
</style>