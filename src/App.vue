<template>
  <div id="app">
    <h1>Todo application</h1>
    <AddTodo
        @add-todo="addTodo"
    />
    <hr>
    <Todolist
    v-bind:todos = "todos"
    @remove-todo="removeTodo"
    />
  </div>
</template>

<script>
import Todolist from "@/components/Todolist"
import AddTodo from "@/components/AddTodo"
export default {
  name: 'App',
  data() {
    return {
      todos: [
        {id: 1, title: 'Купить MacBook Air', completed: true },
        {id: 2, title: 'Купить Tesla Model S', completed: false},
        {id: 3, title: 'Получить работу в IT', completed: false}
      ]
    }
  },
  methods: {
    addTodo(todo) {
      this.todos.push(todo)
    },

    removeTodo(id) {
       this.todos = this.todos.filter( t => t.id !== id)
    }
  },
  components: {
    Todolist, AddTodo

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
</style>
