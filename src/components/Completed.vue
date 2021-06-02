<template>
  <ul class="list-outside md:list-inside">
    <li
      class="flex justify-between item-center"
      v-for="(todolist, index) in TodoLists"
      :key="index"
    >
      <label class="inline-flex items-center mt-3 ">
        <input
          type="checkbox"
          v-model="checkedNames"
          :class="{ done: todolist.done }"
        />
        <span
          class="ml-2 text-white"
          :class="{ done: todolist.done }"
          @click="doneTodo(todolist)"
          >{{ todolist.name }}
          {{ checkedNames }}
        </span>

        <!-- <span
          class="ml-2 text-white"
          >{{ todolist.name }}
          </span> -->
      </label>
      <button
        class="focus:outline-none transform scale-75 uppercase p-3 flex items-center bg-gray-500 hover:bg-gray-400 text-blue-50 max-w-max shadow-sm hover:shadow-lg rounded-full w-12 h-12 "
        @click="Delete(index)"
      >
        <svg
          width="32"
          height="32"
          preserveAspectRatio="xMidYMid meet"
          viewBox="0 0 32 32"
          style="transform: rotate(360deg);"
        >
          <path d="M12 12h2v12h-2z" fill="currentColor"></path>
          <path d="M18 12h2v12h-2z" fill="currentColor"></path>
          <path
            d="M4 6v2h2v20a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V8h2V6zm4 22V8h16v20z"
            fill="currentColor"
          ></path>
          <path d="M12 2h8v2h-8z" fill="currentColor"></path>
        </svg>
      </button>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    TodoLists: Array,
    Delete: Function,
    doneTodo: Function,
  },
  setup() {
    const checkedNames = [];
    return {
      checkedNames,
    };
  },
};
</script>

<style></style>
