<template>
  <main>
    Home
  </main>
</template>

<script>
export default {
  name: 'Home',
  data() {
    return {
    }
  },
  mounted() {

  },
  computed: {
  },
  methods: {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.boardgame {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 1fr);
}

.boardgame div {
  border: 1px solid blue;
  min-height: 30vh;
}
</style>
