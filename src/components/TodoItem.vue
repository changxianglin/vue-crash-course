<template>
  <div class="todo-item" v-bind:class = "{'is-completed': todo.completed}">
    <p>
      <input type="checkbox" v-on:change = "markCompleted">
      {{todo.title}}
      <button @click="$emit('del-todo', todo.id)" class="del">x</button>
    </p>
  </div>
</template>

<script>
  export default {
    name: 'TodoItem',
    props: ["todo"],
    methods: {
      markCompleted() {
        this.todo.completed = !this.todo.completed
      }
    }
  }
</script>

<style scoped>
  .todo-item {
    background-color: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #cccccc dotted;
  }
  .is-completed {
    text-decoration: line-through;
  }
  .del {
    background-color: #ff0000;
    color: #ffffff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }
</style>