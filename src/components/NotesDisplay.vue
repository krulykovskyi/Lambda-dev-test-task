<template>
  <div class="bg-light rounded-3 position-relative">
    <div class="input-group mb-1">
      <input
        v-model="noteTitle"
        type="text"
        class="form-control"
        placeholder="Write note..."
      >
      <button class="btn btn-success" @click="createNote">
        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor" class="bi bi-pen-fill" viewBox="0 0 16 16">
          <path d="m13.498.795.149-.149a1.207 1.207 0 1 1 1.707 1.708l-.149.148a1.5 1.5 0 0 1-.059 2.059L4.854 14.854a.5.5 0 0 1-.233.131l-4 1a.5.5 0 0 1-.606-.606l1-4a.5.5 0 0 1 .131-.232l9.642-9.642a.5.5 0 0 0-.642.056L6.854 4.854a.5.5 0 1 1-.708-.708L9.44.854A1.5 1.5 0 0 1 11.5.796a1.5 1.5 0 0 1 1.998-.001z"/>
        </svg>
      </button>
    </div>

    <note-vue
      v-for="note in notes"
      :key="note.id"
      :note="note"
      @pickNote="this.$emit('pickNote', note)"
      @deleteNote="this.$emit('deleteNote', note)"
    />
  </div>
</template>
<script>
  import NoteVue from "./Note.vue"

  export default {
    components: { NoteVue },

    data() {
      return {
        noteTitle: '',
      }
    },

    props: {
      notes: {
        type: Array,
        required: true
      },
    },

    methods: {
      createNote() {
        if (!this.noteTitle) {
          return;
        }

        const newNote = {
          title: this.noteTitle,
          id: Date.now(),
        };

        this.$emit('createNote', newNote);

        this.noteTitle = '';
      }
    }
  }
</script>
