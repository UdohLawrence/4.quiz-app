<script setup>
  import {RouterView} from 'vue-router';
</script>

<template>
  <div class="container">
    <RouterView />
  </div>
</template>

<style scoped>
.container{
  max-width: 1000px;
  width: 80%;
  margin: 0 auto;
}
@media(max-width:500px){
  .container{
    width: 80%;
    margin: 0 auto;
  }
}
</style>