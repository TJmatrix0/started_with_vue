<template>
  <div id = "app">
    <h1>To-Do List</h1>
    <ul>
      <li v-for = "item in ToDoItems" v-bind:key = "item.id">
        <to-do-item 
        v-bind:label = "item.label" 
        v-bind:done = "item.done" 
        v-bind:id = "item.id"></to-do-item>
      </li>
    </ul>
  </div>
</template>

<script>
import ToDoItem from './components/ToDoItem.vue';
import uniqueId from "lodash.uniqueid";

export default {
  name: 'App',
  components: {
    ToDoItem,
  },
  data() {
    return {
      ToDoItems: [
        { label: "Learn Vue", done: false, id: uniqueId("todo-") },
        { label: "Create a Vue project with the CLI", done: true, id: uniqueId("todo-") },
        { label: "Have fun", done: true, id: uniqueId("todo-") },
        { label: "Create a to-do list", done: false, id: uniqueId("todo-") },
      ],
    };
  },
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
</style>
