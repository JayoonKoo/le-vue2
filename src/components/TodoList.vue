<template>
  <div>
    <ul>
      <li
        v-for="({ compeleted, item }, index) in todoItems"
        v-bind:key="item"
        class="shadow"
      >
        <i
          class="fa fa-check checkBtn"
          v-on:click="toggleComplete(index)"
          v-bind:class="{ checkBtnCompleted: compeleted }"
        ></i>
        <span v-bind:class="{ textCompleted: compeleted }">{{ item }}</span>
        <span class="removeBtn" v-on:click="removeTodo(item, index)">
          <i class="fa fa-trash"></i>
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    todoItems: Array,
    removeTodo: Function,
    toggleComplete: Function,
  },
  created: function () {},
};
</script>

<style scoped>
ul {
  list-style-type: none;
  padding-left: 0px;
  margin-top: 0;
  text-align: left;
}
li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: white;
  border-radius: 5px;
}
.checkBtn {
  line-height: 45px;
  color: #62acde;
  margin-right: 5px;
}
.checkBtnCompleted {
  color: #b3adad;
}
.textCompleted {
  text-decoration: line-through;
  color: #b3adad;
}
.removeBtn {
  cursor: pointer;
  margin-left: auto;
  color: #de4343;
}
</style>
