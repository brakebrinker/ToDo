<template>
    <div id="app">
        <Header />
        <AddTodo v-on:add-todo="addTodo"/>
        <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
    </div>
</template>

<script>
import Header from './components/layout/Header';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';

export default {
    name: 'app',
    components: {
        Header,
        Todos,
        AddTodo,
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
        addTodo(newTodo) {
            this.todos = [...this.todos, newTodo];
        }
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
