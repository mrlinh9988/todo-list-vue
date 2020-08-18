<template>
  <div id="app">
    <router-view />
  </div>
</template>

<script>
// import Header from "./components/layouts/Header";

export default {
  name: "App",
  components: {
    // Header,
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
