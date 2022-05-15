<template>
  <div class="d-flex align-items-center bg-white mb-2 border border-2 rounded p-2">
    <input
      v-if="editing"
      ref="edit"
      @keydown="changeNoteTitle"
      v-model="newTitle"
      type="text"
      class="form-control"
    >

    <span
      v-else
      class="card-body p-1"
      @click="this.$emit('pickNote', note)"
    >
      {{note.title}}
    </span>

    <div class="btn-group">
      <button class="btn btn-outline-success" @click="edit">
        edit
      </button>
      <button class="btn btn-outline-danger" @click="$emit('deleteNote')">
        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor" class="bi bi-trash" viewBox="0 0 16 16">
          <path d="M5.5 5.5A.5.5 0 0 1 6 6v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm2.5 0a.5.5 0 0 1 .5.5v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm3 .5a.5.5 0 0 0-1 0v6a.5.5 0 0 0 1 0V6z"/>
          <path fill-rule="evenodd" d="M14.5 3a1 1 0 0 1-1 1H13v9a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V4h-.5a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1H6a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1h3.5a1 1 0 0 1 1 1v1zM4.118 4 4 4.059V13a1 1 0 0 0 1 1h6a1 1 0 0 0 1-1V4.059L11.882 4H4.118zM2.5 3V2h11v1h-11z"/>
        </svg>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      editing: false,
      newTitle: '',
    }
  },
  props: {
    note: {
      type: Object,
      required: true,
    }
  },
  methods: {
    edit() {
      this.editing = true;
      this.newTitle = this.note.title;
    },

    changeNoteTitle(e) {
      if(e.key !== 'Enter') {
        return;
      }
      
      if(this.newTitle === '') {
        this.editing = false;
        return;
      }

      this.$emit('edit', { ...this.note, title: this.newTitle });
      this.editing = false;
    }
  },
  updated() {
    if(this.editing) {
      this.$refs.edit.focus();
    }
  },
}
</script>
