<template>
  <div>
    <h3>Add Todo</h3>
    <div class="add">
      <form @submit="onSubmit">
        <input class="add-input__text" type="text" v-model="title" placeholder="Add Todo...">
        <input class="add-input__submit" type="submit" value="Submit">
      </form>
    </div>
  </div>
</template>

<script>
import { mapActions } from 'vuex'
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    }
  },
  methods: {
    ...mapActions(['addTodo']),
    onSubmit(e) {
      e.preventDefault();
      this.addTodo(this.title)
    }
  }
}
</script>

<style lang="scss" scoped>
form{
  display: flex;
}
input[type="text"] {
  flex: 10;
  padding: 10px;
  border: 1px solid #41b883;
  outline: 0;
}

input[type="submit"] {
  flex: 2;
  background: #41b883;
  color: #fff;
  border: 1px solid #41b883;
  cursor: pointer;
}
</style>