<template>
  <main>
    <BoardGame></BoardGame>
    <router-link to="/">Revoir les règles</router-link>
  </main>

</template>
<script>
import BoardGame from '@/components/BoardGame.vue'
export default {
  name: "GameView",
  components: {
    BoardGame
  }
}

</script>
<style scoped>
main {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  height: 85vh;
}
</style>