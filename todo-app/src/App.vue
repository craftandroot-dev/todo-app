<template>
  <div id="app">
    <nav>
      <router-link to="/todo">To Do App</router-link>
    </nav>
    <router-view />
  </div>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #0112a9;
    font-size: 20px;

    &.router-link-exact-active {
      color: #000000;
      font-size: 50px;
    }
  }
}
</style>
<script>
export default {
  name: "App",
};
</script>
