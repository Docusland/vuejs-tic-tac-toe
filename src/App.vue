<template>
  <main>
    <router-view />
  </main>
</template>

<style>
body {
  margin: 0
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: #161616;
  color: whitesmoke;
  min-height: 100vh;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}

a,
a:visited,
a:active,
a:focus {
  cursor: pointer;
  color: #42b983;
  font-weight: bold;
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
