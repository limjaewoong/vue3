<template>
  <nav class="navbar">
    <a href="/">HOME</a>
    <a href="/">Movies</a>
    <a href="/">About</a>
  </nav>
</template>

<script>
export default {
  name : 'NavbarComponent',
}
</script>


<style scoped>
.navbar {
  background-color: #000;
  padding: 20px;
}
.navbar a{
  color: #fff;
  text-decoration: none;
  padding: 1em;
}
</style>