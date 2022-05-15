<template lang="">
  <div class="bg-light border border-2 rounded-3">
    <div v-if="note">
  <!-- <todo-form @createTodo="createTodo" />

      <todo-list @deleteTodo="deleteTodo" @changeTodoStatus="changeTodoStatus" :todos="todos" /> -->
    </div>
    <div v-else>choose note</div>
  </div>
</template>

<script>
  export default {
    props: {
      note: {
        type: [Object, null],
        required: true
      }
    }
  }
</script>
