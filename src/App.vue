<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  <header>
      <nav>
        <RouterLink to="/">Home</RouterLink> |
        <RouterLink to="/about">About</RouterLink> |
        <RouterLink to="/todo">AplikasiKu</RouterLink>
      </nav>
  </header>

  <RouterView />
</template>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #070707;
}
nav {
  padding: 30px;
  text-align: center;
}
nav a {
  font-weight: bold;
  color: #070707;
}
nav a.router-link-exact-active {
  color: #8d099e;
}
</style>
