<template>
  <div class="clearAllContainer">
    <span class="clearAllbtn" @click="clearTodo">Clear All</span>
  </div>
</template>

<script>
export default {
  methods: {
    clearTodo() {
      console.log('clearTodo...')
      this.$emit('deleteAllPlease')
      localStorage.clear();
    }

  }
}
</script>

<style>
 .clearAllContainer {
   width: 8.5rem;
   height: 50px;
   line-height: 50px;
   background-color: white;
   border-radius: 5px;
   margin: 0 auto;
 }

  .clearAllbtn {
    color: #e20303;
    display: block;
  }
</style>
