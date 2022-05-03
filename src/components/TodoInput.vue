<template>
  <div class="inputBox shadow">
    <input
      type="text"
      v-model="newTodoItem"
      @keypress.enter="addTodo"
      placeholder="Todos"
    />
    <span class="addContainer" v-on:click="addTodo">
      <i class="fa fa-plus addBtn"></i>
    </span>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      newTodoItem: "",
    };
  },
  methods: {
    addTodo: function () {
      console.log(this.newTodoItem);
      if (this.newTodoItem === "") {
        alert("할일을 입력하세요.");
        return;
      }
      localStorage.setItem(this.newTodoItem, this.newTodoItem);
      this.clearInput();
    },
    clearInput: function () {
      this.newTodoItem = "";
    },
  },
};
</script>

<style scope>
input:focus {
  outline: none;
}
.inputBox {
  background: white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
  display: flex;
  justify-content: space-between;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
  padding-left: 0.9rem;
  width: 85%;
}
.addContainer {
  float: right;
  background: linear-gradient(to right, #6478fb, #8763fb);
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: white;
  vertical-align: middle;
}
</style>
