<template>
  <div>
    <h1>Todo App</h1>
    <div class="container">
      <div class="row">
        <div class="col-lg-12">
          <b-input
            v-model="newTodo"
            placeholder="Enter a new task"
            required
            v-on:keyup.enter="addTodo"
          ></b-input>
        </div>
        
        <div class="col-lg-12">
          <table class="table table-striped mt-3">
            <thead>
              <tr>
                <th scope="col">Task</th>
                <th scope="col">Actions</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(todo, index) in todos" :key="index">
                <td>{{ todo.text }}</td>
                <td>
                  <button
                    @click="removeTodo(index)"
                    class="btn btn-danger btn-sm"
                  >
                    Delete
                  </button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: "",
      todos: [],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() === "") return;
      this.todos.push({ text: this.newTodo, completed: false });
      this.newTodo = "";
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>
