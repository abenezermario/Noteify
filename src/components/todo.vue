<template>
  <div
    class="bg-gray-200 h-screen w-full flex items-center justify-center bg-teal-lightest font-sans"
  >
    <div
      class="bg-yellow-200 rounded shadow p-6 m-4 w-full lg:w-3/4 lg:max-w-lg"
    >
      <div class="mb-4">
        <h1 class="text-grey-darkest">Todo List</h1>
        <div class="flex mt-4">
          <input
            type="text"
            v-model="msg"
            class="shadow appearance-none border rounded w-full py-2 px-3 mr-4 text-grey-darker"
            placeholder="Add Todo"
            @keyup.enter="Create"
          />
          <button
            class="focus:outline-none transform uppercase p-3 flex items-center bg-red-500 text-blue-50 max-w-max shadow-sm hover:shadow-md hover:bg-red-400 rounded-full w-12 h-12 "
            @click="Create"
          >
            <svg
              viewBox="0 0 20 20"
              enable-background="new 0 0 20 20"
              class="w-6 h-6 inline-block"
            >
              <path
                fill="#FFFFFF"
                d="M16,10c0,0.553-0.048,1-0.601,1H11v4.399C11,15.951,10.553,16,10,16c-0.553,0-1-0.049-1-0.601V11H4.601
                                    C4.049,11,4,10.553,4,10c0-0.553,0.049-1,0.601-1H9V4.601C9,4.048,9.447,4,10,4c0.553,0,1,0.048,1,0.601V9h4.399
                                    C15.952,9,16,9.447,16,10z"
              />
            </svg>
          </button>
        </div>
      </div>
      <!-- cancel button -->
      <TodoList :TodoLists="TodoLists" :Delete="Delete" />
    </div>
  </div>
</template>

<script>
import TodoList from "./ListDelete";
import { ref } from "@vue/runtime-core";
export default {
  components: {
    TodoList,
  },
  data() {
    return {
      msg: "",
      newList: [],
      // todo: [{ id: 0, name: "" }],
    };
  },
  setup() {
    let exampleData = [{ id: 1, name: "cooking" }];
    return {
      TodoLists: ref(exampleData),
    };
  },
  computed: {},
  methods: {
    Create() {
      if (this.msg.length !== 0) {
        this.TodoLists.name = "Abuchu";
        console.log(this.TodoLists.value);
        // const next = { id, name: this.msg };
        // this.TodoLists.push(next);
        // console.log(this.TodoLists);
        // this.msg = "";
      } else {
        alert("No input provided!!");
      }
    },
    Delete(idx) {
      console.log(this.TodoLists[idx]);
    },
  },
};
</script>

<style></style>
