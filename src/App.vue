<template>
  <div id="app">
    <h1>TODO LIST</h1>
    <ToDoForm @todo-added="addToDo" />
    <h2 id="list-summary" > {{ listSummary }}</h2>
    <ul aria-labelledby="list-summary" class="stack-large">
      <li v-for="todo in ToDoItems" :key="todo.id" >
        <ToDoItem :label="todo.label" :done="todo.done" :id="todo.id"
        @checkbox-changed="updateDoneStatus(todo.id)"
        @item-edited="editToDo(todo.id, $event)"
        @item-deleted="deleteToDo(todo.id)" />
      </li>
    </ul>
  </div>
</template>

<script>
import ToDoItem from './components/ToDoItem';
import ToDoForm from './components/ToDoForm';

import uniqueId from 'lodash.uniqueid';

export default {
  name: 'App',
  components: {
    ToDoItem,
    ToDoForm
  },
  data() {
    return {
      ToDoItems: [
        {id: uniqueId("todo-") ,  label: "Set up basic vue app", done: true},
        {id: uniqueId("todo-") ,  label: "Learned about props and state", done: true},
        {id: uniqueId("todo-") ,  label: "Vue life cycle", done: false}
      ]
    }
  },
  methods: {
    addToDo(todoLabel) {
      console.log("add", todoLabel);
      this.ToDoItems.push(
        {id: uniqueId('todo-'), label: todoLabel, done: false }
      );
    },
    updateDoneStatus(id) {
      const itemToUpdate = this.ToDoItems.find(item => item.id == id); // returns perticular object to update
      itemToUpdate.done = !itemToUpdate.done;
    },
    editToDo(id, newLabel) {
      let toDoToEdit = this.ToDoItems.find(item => item.id === id);
      toDoToEdit.label = newLabel;
    },
    deleteToDo(id) {
      console.log(id);
      let indexToDelete = this.ToDoItems.findIndex(item => item.id === id);
      this.ToDoItems.splice(indexToDelete, 1);
    }
    
  },
  computed: {
    listSummary(){
      const numberFinishedItem = this.ToDoItems.filter(item => item.done).length;
      return `${numberFinishedItem} finished out of ${this.ToDoItems.length}`;
    }
  }
}
</script>

<style>
/* Global styles */
.btn {
  padding: 0.8rem 1rem 0.7rem;
  border: 0.2rem solid #4d4d4d;
  cursor: pointer;
  text-transform: capitalize;
}
.btn__danger {
  color: #fff;
  background-color: #ca3c3c;
  border-color: #bd2130;
}
.btn__filter {
  border-color: lightgrey;
}
.btn__danger:focus {
  outline-color: #c82333;
}
.btn__primary {
  color: #fff;
  background-color: #000;
}
.btn-group {
  display: flex;
  justify-content: space-between;
}
.btn-group > * {
  flex: 1 1 auto;
}
.btn-group > * + * {
  margin-left: 0.8rem;
}
.label-wrapper {
  margin: 0;
  flex: 0 0 100%;
  text-align: center;
}
[class*="__lg"] {
  display: inline-block;
  width: 100%;
  font-size: 1.9rem;
}
[class*="__lg"]:not(:last-child) {
  margin-bottom: 1rem;
}
@media screen and (min-width: 620px) {
  [class*="__lg"] {
    font-size: 2.4rem;
  }
}
.visually-hidden {
  position: absolute;
  height: 1px;
  width: 1px;
  overflow: hidden;
  clip: rect(1px 1px 1px 1px);
  clip: rect(1px, 1px, 1px, 1px);
  clip-path: rect(1px, 1px, 1px, 1px);
  white-space: nowrap;
}
[class*="stack"] > * {
  margin-top: 0;
  margin-bottom: 0;
}
.stack-small > * + * {
  margin-top: 1.25rem;
}
.stack-large > * + * {
  margin-top: 2.5rem;
}
@media screen and (min-width: 550px) {
  .stack-small > * + * {
    margin-top: 1.4rem;
  }
  .stack-large > * + * {
    margin-top: 2.8rem;
  }
}
/* End global styles */
#app {
  background: #fff;
  margin: 2rem 0 4rem 0;
  padding: 1rem;
  padding-top: 0;
  position: relative;
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.2), 0 2.5rem 5rem 0 rgba(0, 0, 0, 0.1);
}
@media screen and (min-width: 550px) {
  #app {
    padding: 4rem;
  }
}
#app > * {
  max-width: 50rem;
  margin-left: auto;
  margin-right: auto;
}
#app > form {
  max-width: 100%;
}
#app h1 {
  display: block;
  min-width: 100%;
  width: 100%;
  text-align: center;
  margin: 0;
  margin-bottom: 1rem;
}

</style>
