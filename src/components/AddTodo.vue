<template>
  <div>
    <form v-on:submit.prevent="addTodo">
      <input type="text" v-model="title" name="title" placeholder="Add todo" />
      <input type="submit" value="Add Todo" class="btn" />
    </form>
  </div>
</template>


<script>
export default {
  name: "AddTodo",
  data: function () {
    return {
      title: "",
    };
  },
  methods: {
    addTodo: function () {
      // Có 2 cách chặn form reload lại trang trong Vuejs:
      // Cách 1: event.preventDefault();
      // Cách 2: thêm trực tiêps v-on:submit.prevent
      const newTodo = {
        title: this.title,
        completed: false,
      };
      // send up to parent
      this.$emit("add-todo", newTodo);
      this.title = ""; // reset input value
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
}
input[type="text"] {
  flex: 10;
  padding: 5px;
}
input[type="submit"] {
  flex: 2;
}
</style>