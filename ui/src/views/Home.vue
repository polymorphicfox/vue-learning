<template>
  <div id="app">
    <AddTodoItem v-on:todo-created="addTodoItem"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodoItem"/>
  </div>
</template>

<script>
  import Todos from "../components/Todos";
  import AddTodoItem from "../components/AddTodoItem";
  import axios from 'axios';

  export default {
    name: 'home',
    components: {
      Todos,
      AddTodoItem
    },
    data() {
      return {
        todos: []
      }
    },
    methods: {
      deleteTodoItem(id) {
        axios.delete('https://jsonplaceholder.typicode.com/todos/${id})')
                .then(response => {
                  this.todos = this.todos.filter(todo => todo.id !== id)
                })
      },
      addTodoItem(newTodo) {
        const {title, completed} = newTodo;

        axios.post('https://jsonplaceholder.typicode.com/todos', {
          title,
          completed
        })
                .then(response => {
                  this.todos = [...this.todos, response.data]
                })
                .catch(err => console.log(err))
      }
    },
    created() {
      axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
              .then(response => {
                this.todos = response.data
              })
              .catch(err => console.log(err))
    }
  }
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }

  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover {
    background: #666;
  }
</style>
