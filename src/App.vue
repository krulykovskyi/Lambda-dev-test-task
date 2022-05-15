<template>
  <div class="todo-app h-100">
    <app-header />

    <div class="container-fluid p-3 h-100">
      <div class="d-grid gap-3 h-100" style="grid-template-columns: 2fr 3fr;">
        <notes-display
          :notes="notes"
          @createNote="createNote"
          @pickNote="pickNote"
          @deleteNote="deleteNote"
          @edit="editNote"
        />
        <picked-note :note="pickedNote"/>
      </div>
    </div>
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue"
import PickedNote from "./components/PickedNote.vue";
import NotesDisplay from "./components/NotesDisplay.vue";
import TodoForm from "@/components/TodoForm.vue";
import TodoList from "@/components/TodoList.vue";

export default {
  components: {
    AppHeader, TodoForm, TodoList, NotesDisplay, PickedNote
  },

  data() {
    return {
      notes: [
        { title: 'gggg', id: 1},
        { title: 'dddd', id: 2},
        { title: 'ggxzcvz', id: 3}
      ],
      pickedNote: null,

      todos: [
        { id: 1, title: 'clean my room', body: 'clean all my room everywhere', completed: true },
        { id: 2, title: 'cook dinner', body: 'cook some pasta for dinner', completed: false },
        { id: 3, title: 'study programming', body: 'do much practice with redux', completed: false },
      ],
    }
  },

  methods: {
    createNote(note) {
      this.notes.push(note);
    },

    deleteNote(note) {
      this.notes = this.notes.filter(n => n.id !== note.id);
    },

    editNote(note) {
      console.log(note);
      this.notes = this.notes.map(n => n.id !== note.id ? n : note);
    },

    pickNote(note) {
      this.pickedNote = this.notes.find(n => n.id = note.id);
    },

    createTodo(todo) {
      this.todos.push(todo);
    },

    deleteTodo(todoId) {
      this.todos = this.todos.filter(todo => todo.id !== todoId);
    },

    changeTodoStatus(todoId) {
      this.todos = this.todos.map(todo => todo.id !== todoId ? todo : { ...todo, completed: !todo.completed});
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Courgette&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  height: 80vh;
  --sexy-purple: #6A0DAD;
  --sexy-yellow: #FFCC00;
}

</style>