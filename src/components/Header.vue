<template>
  <div class="header">
    <h1>DINOSAUR SCORE</h1>
  </div>
</template>

<script>
export default {
  name: 'Header',
};
</script>

<style scoped>
.header {
  background-image: url('~@/assets/d-header.jpg');
}
h1 {
  margin: 0;
  padding: 1rem;
  color: white;
  font-family: 'Griffy', cursive;
}
</style>
