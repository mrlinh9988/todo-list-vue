<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteItem" />
  </div>
</template>

<script>
import Todos from '../components/Todos';
import Header from '../components/layouts/Header';
import AddTodo from '../components/AddTodo';
import axios from 'axios';

export default {
  name: 'Home',
  components: {
    Todos,
    Header,
    AddTodo,
  },
  data: function() {
    return {
      todos: [],
    };
  },
  methods: {
    deleteItem: function(id) {
      axios
        .delete(`http://localhost:3000/todo/${id}`)
        .then(() => (this.todos = this.todos.filter((todo) => todo._id !== id)))
        .catch((error) => console.log(error));
    },
    addTodo: function(newTodo) {
      const { title, completed } = newTodo;
      axios
        .post('http://localhost:3000/todo', {
          title,
          completed,
        })
        .then((res) => (this.todos = [...this.todos, res.data.newTodo]))
        .catch((error) => console.log(error));
    },
  },
  created: function() {
    axios
      .get('http://localhost:3000/todo')
      .then((res) => {
        console.log('res: ', res);
        return (this.todos = res.data.allTodos);
      })
      .catch((error) => console.log(error));
  },
};
</script>

<style>
* {
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
