<template lang="">
  <header class="d-flex py-2 px-3 mb-2 border-bottom bg-white">
    <a href="#" class="header_logo d-flex align-items-center text-decoration-none rounded-circle">
      <img src="../assets/logo.svg" alt="my notes logo">
    </a>
    <h1 class="header_title d-flex justify-content-center align-items-center me-auto ms-3 mb-0">
      MyNotes 🤔💡📝
    </h1>
    <div class="d-flex align-items-center w-40">
      <input type="search" class="form-control" placeholder="Search notes...">
    </div>
  </header>
</template>

<script>
export default {
  
}
</script>

<style scoped>
  .header_logo {
    width: 70px;
    background-color: var(--sexy-yellow);
  }
  .header_logo img {
    width: 100%;
    height: 55%;
  }
  .header_title {
    min-width: 230px;
    color: var(--sexy-purple);
    font-family: 'Courgette', cursive;
  }
  .w-40 {
    width: 40%
  }
</style>