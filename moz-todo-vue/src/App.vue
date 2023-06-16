<template>
  <div id = "app">
    <h1>To-Do List</h1>
    <to-do-form v-on:todo-added = "addToDo"></to-do-form>
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
import ToDoForm from './components/ToDoForm.vue';
import uniqueId from "lodash.uniqueid";

export default {
  name: 'App',
  components: {
    ToDoItem,
    ToDoForm,
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
  methods: {
    addToDo(toDoLabel) {
      console.log("To-do added.", toDoLabel);
      this.ToDoItems.push({label: toDoLabel, done: false, 
      id:uniqueId('todo-')});
    }
  }
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
