<template>
  <Form />
</template>

<script>
import Form from "./components/SignUpForm.vue"

export default {
  name: 'App',
  components: {Form}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  margin: 0;
  background-color: #eee;
}
</style>
