<template>
  <div class="todoapp">
    <div class="enterTodo flex">
      <input
        v-model="newTodo"
        type="text"
        placeholder="What is the new task?"
        class="border-4 border-l-blue-700 w-1/3 focus:outline-none focus:shadow-outline"
      /><svg
        @click="todos.push(newTodo)"
        xmlns="http://www.w3.org/2000/svg"
        class="addTask first-line:h-6 w-6 cursor-pointer"
        viewBox="0 0 22 22"
        stroke="currentColor"
        stroke-width="2"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M12 9v3m0 0v3m0-3h3m-3 0H9m12 0a9 9 0 11-18 0 9 9 0 0118 0z"
        />
      </svg>
    </div>
    <div class="todoList w-1/3 mt-11">
      <ul>
        <li
          class="w-2/3 ml-12 flex"
          v-for="(todo, index) in todos"
          :key="index">
          {{ todo}}
          <svg
            @click="removeTask(todos)"
            xmlns="http://www.w3.org/2000/svg"
            class="removeTask h-6 w-6 cursor-pointer"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            stroke-width="2"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M15 12H9m12 0a9 9 0 11-18 0 9 9 0 0118 0z"
            />
          </svg>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "Todoapp",
  data() {
    return {
      todos: ["Learn Vue", "Learn Vuex", "Learn Vue Router"],
    };
  },
  methods: {
    removeTask: function (todo) {
      var index = this.todos.indexOf(todo);
      this.todos.splice(index);
    },
  },
};
</script>
