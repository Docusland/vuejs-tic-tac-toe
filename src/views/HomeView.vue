<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <p>
      Jeu qui se joue à deux joueurs, sur un damier de 3 cases par 3 cases.
      Chaque joueur est représenté par un "symbole"
      Un joueur utilise toujours le même type de "symbole". Soit un X, soit un O.
      Un premier joueur dessine son symbole sur une case. Puis c'est au tour de l'autre joueur de dessiner son symbole
      sur une case vide.
      Le but du jeu est de réussir à aligner ses trois symboles (horizontal, vertical ou diagonale), on remporte alors
      la partie. Si la grille est remplie et qu'aucune ligne ne comporte trois symboles identiques, les joueurs
      finissent par un
      match nul.
    </p>
    <router-link to="/game">Jouer</router-link>
  </div>
</template>

<script>
// @ is an alias to /src
export default {
  name: 'HomeView',
  components: {
  }
}
</script>
<style scoped>
p {
  margin: 2em;
}
</style>
