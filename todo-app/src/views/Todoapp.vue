<template>
  <div class="todoapp">
    <div class="enterTodo">
      <input
        ref="muhiddin"
        v-model="newTodoText"
        type="text"
        placeholder="What is the new task?"
        class="border-4 border-l-blue-700 focus:outline-none focus:shadow-outline w-96"
      /><svg
        @click="addTodo(newTodoText)"
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
    <div class="todoList mt-11">
      <table class="w-4/12">
        <tr>
          <th>Task</th>
          <th>Remove</th>
          <th>Checked</th>
          <th>Edit</th>
        </tr>
        <tr
          v-for="(todo, index) in todos"
          :key="index"
          :class="{ line: todo.checked }"
        >
          <td v-if="!todo.editMode">
            {{ todo.text }}
          </td>
          <td v-else>
            <input
              type="text"
              v-model="editedText"
              @keyup.enter="confirmEditedTask(todo, index)"
            />
          </td>
          <td>
            <svg
              @click="removeTask(index)"
              xmlns="http://www.w3.org/2000/svg"
              class="removeTask h-6 w-6 cursor-pointer ml-10"
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
          </td>
          <td>
            <input type="checkbox" v-model="todo.checked" class="mt-1.5 ml-2" />
          </td>
          <td>
            <svg
              @click="editTask(todo)"
              xmlns="http://www.w3.org/2000/svg"
              class="h-6 w-6 ml-5 cursor-pointer"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
              stroke-width="2"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M15.232 5.232l3.536 3.536m-2.036-5.036a2.5 2.5 0 113.536 3.536L6.5 21.036H3v-3.572L16.732 3.732z"
              />
            </svg>
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "Todoapp",
  data() {
    return {
      todos: [
        {
          text: "Learn Vue",
          checked: false,
          editMode: false,
        },
        {
          text: "Learn Vuex",
          checked: false,
          editMode: false,
        },
        {
          text: "Learn Vue Router",
          checked: false,
          editMode: false,
        },
      ],
      newTodoText: "",
      editedText: "",
    };
  },
  mounted() {
    let newTodos = localStorage.getItem("todo");
    if (newTodos.length) {
      this.todos = JSON.parse(newTodos) || [];
    }
  },
  methods: {
    // remove task
    removeTask(index) {
      this.todos.splice(index, 1);
      localStorage.setItem("todo", JSON.stringify(this.todos));
    },
    // add new task
    addTodo(text) {
      if (this.newTodoText !== "") {
        this.todos.push({
          text: text,
          checked: false,
          editMode: false,
        });
        localStorage.setItem("todo", JSON.stringify(this.todos));
        this.newTodoText = "";
      } else {
        alert("Don't add empty task");
      }
    },
    // open input to edit task
    editTask(todo) {
      todo.editMode = true;
    },
    // save edited task
    confirmEditedTask(todo, index) {
      this.todos[index].text = this.editedText;
      todo.editMode = false;
      localStorage.setItem("todo", JSON.stringify(this.todos));
    },
  },
};
</script>
