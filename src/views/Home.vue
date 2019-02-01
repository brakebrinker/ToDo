<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
    import Todos from '../components/Todos';
    import AddTodo from '../components/AddTodo';
    import axios from 'axios';

    export default {
        name: 'Home',
        components: {
            Todos,
            AddTodo,
        },
        data() {
            return {
                todos: [],
            }
        },
        methods: {
            deleteTodo (id) {
                axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
                    .then(result => this.todos = this.todos.filter(todo => todo.id !== id))
                    .catch(error => console.log(error));
            },
            addTodo(newTodo) {
                const {title, completed} = newTodo;

                axios.post('https://jsonplaceholder.typicode.com/todos', {
                    title,
                    completed,
                })
                    .then(result => this.todos = [...this.todos, result.data])
                    .catch(error => console.log(error));

                ;
            }
        },
        created() {
            axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
                .then(result => this.todos = result.data)
                .catch(error => console.log(error));
        }
    }
</script>

<style>
  * {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
  }

  body {
    font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
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
