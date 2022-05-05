<template>
  <button class="clearAllBtn" v-on:click="removeAll">Clear All</button>
</template>

<script>
export default {
  methods: {
    removeAll: function () {
      localStorage.clear();
      this.$emit("removeAll");
    },
  },
};
</script>

<style scoped>
.clearAllBtn {
  width: 8.5rem;
  height: 50px;
  line-height: 50px;
  background-color: white;
  border-radius: 5px;
  margin: 0 auto;
  color: #e20303;
  border: none;
  cursor: pointer;
  transition: all 0.2s;
}
.clearAllBtn:hover {
  filter: brightness(0.95);
}
.clearAllBtn:active {
  background: #ca92929a;
}
</style>
