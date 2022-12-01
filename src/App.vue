<template>
  <div id="app">
    <div class="container">
      <AddTodo/>
      <FiterTodos />
      <TodosList/>
    </div>
  </div>
</template>

<script>
import TodosList from './components/TodosList.vue'
import AddTodo from './components/AddTodo.vue'
import FiterTodos from './components/FiterTodos.vue'

export default {
  name: 'App',
  components: {
    TodosList,
    AddTodo,
    FiterTodos
  }
}
</script>

<style lang="scss" scoped>
body{
  line-height: 1.6;
  background: #e8f7f0;
}

.container{
  min-width: 1100px;
  margin: auto;
  overflow: auto;
  padding: 0 2rem;
}
</style>
