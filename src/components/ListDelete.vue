<template>
  <div>
    <ul>
      <li v-for="(todos, index) in Todolist" :key="index">
        <span>{{ todos.content }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    Todolist: Array,
  },
};
</script>

<style></style>
