<template>
  <div class="app">
    <AddTodos v-on:add-todo = "addTodo" />
    <Todos v-bind:todos = "todos" v-on:del-todo = "deleteTodo"  />
  </div>
</template>

<script>
import Todos from '../components/Todos'
import AddTodos from '../components/AddTodo'

import axios from 'axios'

export default {
  name: 'home',
  components: {
    Todos,
    AddTodos
  },
  data(){
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(res => this.todos = this.todos.filter(todo => todo.id !== id))
        .catch(err => console.log(err))
    },
    addTodo(newTodo) {
      const { title , completed } = newTodo
      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
        .then(res => this.todos = [...this.todos, res.data])
        .catch(err => console.log(err))
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err))
  }
}
</script>

<style scoped>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }
</style>
