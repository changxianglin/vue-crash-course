<template>
  <header class="header">
    <h1>TodoList</h1>
    <div class="nav">
      <router-link to = '/'>Home</router-link>
      <router-link to = '/about'>About</router-link>
    </div>
  </header>
</template>

<script>
  export default {
    name: "Header",
  }
</script>

<style scoped>
  .header {
    background: #333;
    color: #ffffff;
    text-align: center;
    padding: 10px;
  }
  .header a {
    color: #ffffff;
    padding-left: 5px;
    text-decoration: none;
  }
  
</style>