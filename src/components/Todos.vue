<template>
  <div>
    <div>
      <h3 v-for="todo in todos" v-bind:key="todo._id">
        <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo._id)" />
      </h3>
    </div>
  </div>
</template>

<script>
import TodoItem from './TodoItem';

export default {
  name: 'Todos',
  props: ['todos'],
  components: {
    TodoItem,
  },
};
</script>

<style scoped></style>
