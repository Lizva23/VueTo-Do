<template>
  <h1>{{ title }}</h1>
  <Todo />
</template>

<script>
import Todo from './components/Todo.vue'

export default {
  name: 'App',
  components: { Todo },
  data(){
    return{
      title: 'my first vue website.',
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
</style>
