<template>
    <div id="app">
        <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
    </div>
</template>

<script>
import Todos from './components/Todos';

export default {
    name: 'app',
    components: {
        Todos,
    },
    data() {
        return {
            todos: [
                {
                    id: 1,
                    title: "TODO One",
                    completed: false,
                },
                {
                    id: 2,
                    title: "TODO Two",
                    completed: true,
                },
                {
                    id: 3,
                    title: "TODO Three",
                    completed: false,
                },
            ]
        }
    },
    methods: {
        deleteTodo (id) {
            this.todos = this.todos.filter(todo => todo.id !== id);
        },
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
</style>
