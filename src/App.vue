<template>
  <div id="app">
    <h1>ToDo List</h1>
    <ToDoForm />

  </div>
</template>

<script>
import ToDoForm from './components/ToDoForm.vue'

export default {
  name: 'App',
  components: {
    ToDoForm
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

/* #body {
  background-color: #1E2626;
  color: white;
} */
</style>
