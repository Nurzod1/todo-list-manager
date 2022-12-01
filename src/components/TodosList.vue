<template>
  <div>
    <h3>Todos</h3>
    <div class="legend">
      <span>Doouble ckick to amrk as complete</span>
      <span>
        <span class="incomplete-box"></span> = Incomplete
      </span>
      <span>
        <span class="complete-box"></span> = Complete
      </span>
    </div>
    <div class="todos">
      <div 
      @dblclick="onDblClick(todo)"
      v-for="todo in allTodos" 
      :key="todo.id" 
      class="todo"
      v-bind:class="{'is-complete':todo.completed}">
        {{ todo.title }}
        <button 
        class="todos-delete"
        @click="deleteTodo(todo.id)"
        >
          <svg xmlns="http://www.w3.org/2000/svg" height="20" width="20"><path d="M6.5 17q-.625 0-1.062-.438Q5 16.125 5 15.5v-10H4V4h4V3h4v1h4v1.5h-1v10q0 .625-.438 1.062Q14.125 17 13.5 17Zm7-11.5h-7v10h7ZM8 14h1.5V7H8Zm2.5 0H12V7h-1.5Zm-4-8.5v10Z"/></svg>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex';

export default {
  name: 'todos-list',
  methods: {
    ...mapActions(['fetchTodos', 'deleteTodo', 'updateTodo']),
    onDblClick(todo) {
      const updTodo = {
        id: todo.id,
        title: todo.title,
        completed: !todo.completed
      }


      this.updateTodo(updTodo)
    }
  },
  computed: mapGetters(['allTodos']),
  created() {
    this.fetchTodos()
  }
}
</script>

<style lang="scss" scoped>
.todos{
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 1rem;

  &-delete{
   border: none;
   background-color: transparent;
   cursor: pointer;
   position: absolute;
   bottom: 10px;
   right: 10px;
  }
}

.todo{
  border: 1px solid #ccc;
  background: #41b883;
  padding: 1rem;
  border-radius: 5px;
  text-align: center;
  position: relative;
  cursor: pointer;
}

.legend{
  display: flex;
  justify-content: space-around;
  margin-bottom: 1rem;
}

.complete-box{
  display: inline-block;
  width: 10px;
  height: 10px;
  background: #35495e;
}

.incomplete-box{
  display: inline-block;
  width: 10px;
  height: 10px;
  background: #41b883;
}

.is-complete{
  background-color: #35495e;
  color: #fff;
}

@media (max-width: 500px) {
  .todos {
    grid-template-columns: 1fr;
  }
}
</style>