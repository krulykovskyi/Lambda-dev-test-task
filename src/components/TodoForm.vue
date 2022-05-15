<template>
  <form
    action=""
    @submit.prevent
  >
    <input
      v-model="todo.title"
      class="form-control"
      type="text"
      placeholder="todo title"
    >
    <input
      v-model="todo.body"
      class="form-control"
      type="text"
      placeholder="todo description"
    >
    <button
      @click="createTodo"
      class="btn btn-outline-success"
    >
      add todo
    </button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      todo: {
        title: '',
        body: '',
        completed: false
      }
    }
  },
  methods: {
    createTodo() {
      this.todo.id = Date.now();
      this.$emit('createTodo', this.todo);

      this.todo = {
        title: '',
        body: '',
        completed: false
      };
    },
  }
}
</script>
