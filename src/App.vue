<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="AddTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Header from './components/layout/Header.vue';
import Todos from './components/Todos.vue';
import AddTodo from './components/AddTodo.vue';

export default {
  name: 'App',
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
          title: 'Todo One',
          completed: false,

        },
        {
          id: 2,
          title: 'Todo Two',
          completed: true,
        },
        {
          id: 3,
          title: 'Todo Three',
          completed: false,
        },
      ],
    };
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },

    AddTodo(newTodo) {
      this.todos = [...this.todos, newTodo]; // spread op to copy this.todos into newTodos
    },
  },
};
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0 ;
    padding: 0 ;
  }

  body  {
    font-family: sans-serif;
    line-height: 1.6;
  }

  .btn {
    display: inline-block;
    border: none;
    background: #555 ;
    color:#fff ;
    padding: 7px 20px ;
    cursor: pointer;
  }

  .btn:hover {
    background: #666
  }
</style>
