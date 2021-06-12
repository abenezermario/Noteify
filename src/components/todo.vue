<template>
  <div
    class="flex-col bg-gray-800 h-screen w-screen flex items-center justify-center font-sans"
  >
    <div class="bg-gray-600 rounded shadow p-6 m-4 w-full lg:w-3/4 lg:max-w-lg">
      <div class="mb-4">
        <h1 class="text-white">Todo List</h1>
        <!-- <div class="flex mt-4"> -->
        <form class="flex mt-4" @submit.prevent="addTodo()">
          <input
            class="border border-gray-800 focus:border-blue-500 rounded w-full py-2 px-3 mr-4 text-black"
            placeholder="Add Todo"
            v-model="newTodo"
          />
          <!-- Add button -->
          <button
            class="p-0 w-12 h-10 bg-gray-500 rounded-full hover:bg-gray-400 active:shadow-lg mouse shadow transition ease-in duration-200 focus:outline-none"
            @click="addTodo()"
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
        </form>
        <!-- </div> -->
      </div>
      <div>
        <div class="flex mb-4 items-center">
          <p class="w-full text-white">
            <completed
              :TodoLists="todos"
              :Delete="Delete"
              :toggleTodo="toggleTodo"
            />
          </p>
        </div>
      </div>
    </div>
    <!-- End of file -->
  </div>
</template>

<script>
import { ref } from "vue";
import completed from "./Completed";
export default {
  components: {
    completed,
  },
  setup() {
    const newTodo = ref("");
    const checked = ref([]);
    const drag = false;
    const defaultData = [
      {
        done: false,
        name: "Write a blog post",
      },
    ];
    const todos = ref(defaultData);
    function addTodo() {
      if (newTodo.value) {
        todos.value.push({
          done: false,
          name: newTodo.value,
        });
        newTodo.value = "";
        //  console.log(typeof(todos.value))
      }
    }

    function Delete(idx) {
      todos.value.splice(idx, 1);
    }

    function toggleTodo(todos) {
      todos.done = !todos.done;

      checked.value.push({ done: todos.done, name: todos.name });
      console.log(checked.value);
    }

    function reopentodo(completedItems) {
      console.log(completedItems);
      // todos.done = !todos.done;
    }
    return {
      todos,
      addTodo,
      newTodo,
      Delete,
      checked,
      toggleTodo,
      reopentodo,
      drag,
    };
  },
};
</script>

<style></style>
