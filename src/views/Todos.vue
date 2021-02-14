<template>
  <div>
    <h2>To do app</h2>
    <AddTodo @add-todo="addTodo"/>
    <hr>
    <TodoList v-bind:todos="todos" @remove-todo="removeTodo"/>
  </div>
</template>
<!--<script>-->
<!--export default {-->
<!--name: "Todos"-->
<!--}-->
<!--</script>-->

<script>
import TodoList from "@/components/TodoList";
import AddTodo from "@/components/AddTodo";
export default {
  name: 'todos',
  data() {
    return {
      todos: []
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
        .then(response => response.json())
        .then(json => this.todos=json)
  },
  components: {
    TodoList, AddTodo
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(t =>t.id !== id)
    },
    addTodo(todo) {
      this.todos.push(todo)
    }
  }
}
</script>

<style scoped>

</style>