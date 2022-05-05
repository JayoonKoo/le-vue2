<template>
  <div id="app">
    <TodoHeader />
    <TodoInput v-on:addOneItem="addItem" />
    <TodoList v-bind="{ todoItems, removeTodo, toggleComplete }" />
    <TodoFooter v-on:removeAll="removeAll" />
  </div>
</template>

<script>
import TodoHeader from "./components/TodoHeader.vue";
import TodoFooter from "./components/TodoFooter.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";

export default {
  data: function () {
    return {
      todoItems: [],
    };
  },
  created: function () {
    for (let i = 0; i < localStorage.length; i++) {
      const savedTodo = getLocalStorageByIndex(i);
      this.todoItems.push(savedTodo);
    }
  },
  components: {
    TodoHeader,
    TodoFooter,
    TodoInput,
    TodoList,
  },
  methods: {
    removeTodo: function (todoItem, index) {
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },
    toggleComplete: function (index) {
      toggleLocalStorageByIndex(index);
      this.todoItems[index].compeleted = !this.todoItems[index].compeleted;
    },
    addItem: function (todo) {
      const addTodo = { compeleted: false, item: todo };
      localStorage.setItem(todo, JSON.stringify(addTodo));
      this.todoItems.push(addTodo);
    },
    removeAll: function () {
      this.todoItems = [];
    },
  },
};

function getLocalStorageByIndex(index) {
  const todoByIndex = localStorage.getItem(localStorage.key(index));
  return JSON.parse(todoByIndex);
}

function toggleLocalStorageByIndex(index) {
  const todo = getLocalStorageByIndex(index);
  todo.compeleted = !todo.compeleted;
  localStorage.setItem(localStorage.key(index), JSON.stringify(todo));
}
</script>

<style>
body {
  text-align: center;
  background-color: #f6f6f6;
}
input {
  border-style: groove;
}
button {
  border-style: groove;
}
.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>
