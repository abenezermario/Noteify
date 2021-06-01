<template>
  <div>
    <p>{{ message }}</p>

    <completeTodo :completeTodo="completeTodo" />
    <button class="bg-red-300 border" @click="completeTodo(id)">
      Click me
    </button>
  </div>
</template>

<script>
import completeTodo from "./ListDelete";
export default {
  components: {
    completeTodo,
  },
  props: {
    message: String,
    Completed: Function,
  },
  setup() {
    return {};
  },
  completeTodo: function() {},
};
</script>

<style></style>
