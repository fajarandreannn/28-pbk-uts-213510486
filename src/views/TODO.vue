<script setup>
import { ref, computed } from "vue";

let id = 0;
const newTodo = ref("");
const hideCompleted = ref(true);
const todos = ref([
  { id: id++, text: "course java", done: true },
  { id: id++, text: "course html", done: false },
]);
const filteredTodos = computed(() => {
  return hideCompleted.value ? todos.value.filter((t) => !t.done) : todos.value;
});
function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value, done: false });
  newTodo.value = "";
}
function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo);
}
</script>

<template>
  <div class="container mx-auto px-20">
    <div class="justify-center py-10 mt-6 mx-6">
      <h1 class="uppercase font-bold text-3xl text-center pb-4">
        List Kegiatan
      </h1>
      <form @submit.prevent="addTodo">
        <div class="mb-6 px-10">
          <label class="block mb-2 text-sm font-medium text-gray-900"
            >Tambah Kegiatan</label
          >
          <input
            v-model="newTodo"
            type="text"
            placeholder="Tambahkan Kegiatan..."
            class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-purple-500 focus:border-purple-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-purple-500 dark:focus:border-purple-500"
          />
        </div>
        <button
          type="submit"
          class="mx-10 text-white bg-purple-700 hover:bg-purple-800 focus:ring-4 focus:outline-none focus:ring-purple-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center"
        >
          Submit
        </button>
      </form>
      <div class="relative overflow-x-auto sm:rounded-lg mx-10 my-10">
        <ul class="list-none flex-row mx-auto">
          <li
            v-for="todo in filteredTodos"
            :key="todo.id"
            class="p-2 font-medium text-gray-900"
          >
            <div
              class="flex items-center justify-center bg-purple-400 rounded py-2"
            >
              <span :class="{ done: todo.done }">{{ todo.text }}</span>
              <input
                class="ml-2 w-4 h-4 text-purple-600 bg-gray-100 border-gray-300 rounded focus:ring-purple-500 focus:ring-2"
                type="checkbox"
                v-model="todo.done"
              />
              <button class="ml-2 text-purple-950" @click="removeTodo(todo)">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke-width="1.5"
                  stroke="currentColor"
                  class="w-6 h-6"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M14.74 9l-.346 9m-4.788 0L9.26 9m9.968-3.21c.342.052.682.107 1.022.166m-1.022-.165L18.16 19.673a2.25 2.25 0 01-2.244 2.077H8.084a2.25 2.25 0 01-2.244-2.077L4.772 5.79m14.456 0a48.108 48.108 0 00-3.478-.397m-12 .562c.34-.059.68-.114 1.022-.165m0 0a48.11 48.11 0 013.478-.397m7.5 0v-.916c0-1.18-.91-2.164-2.09-2.201a51.964 51.964 0 00-3.32 0c-1.18.037-2.09 1.022-2.09 2.201v.916m7.5 0a48.667 48.667 0 00-7.5 0"
                  />
                </svg>
              </button>
            </div>
          </li>
        </ul>
      </div>
      <button
        class="mx-10 text-white bg-purple-700 hover:bg-purple-800 focus:ring-4 focus:outline-none focus:ring-purple-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center"
        @click="hideCompleted = !hideCompleted"
      >
        {{ hideCompleted ? "Tampilkan Semua" : "Tampilkan yang belum selesai" }}
      </button>
    </div>
    <h1 class="text-center font-bold">©fajarandreanpratama</h1>
  </div>
</template>

<style scoped>
.done {
  text-decoration: line-through;
}
</style>
