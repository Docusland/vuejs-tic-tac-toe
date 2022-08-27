<template>
  <main>
    <div v-if="!winner">
      <div class="info">Joueur {{ currentPlayerSymbol }} : C'est à vous de jouer</div>
      <div class="boardgame">
        <div @click="clickedOnCell" v-for="i in nb_cells" :key="i" :data-value="i">
        </div>
      </div>
    </div>
    <div v-if="winner">
      <div>
        <span v-if="winner != noWinner">Le joueur {{ winner }} a gagné !</span>
        <span v-else> Aucun vainqueur ce tour ci.</span>
      </div>
      <a v-on:click="reload">🗘 Rejouer</a>
    </div>
  </main>
</template>

<script>
export default {
  name: 'BoardGame',
  props: {
    cols: {
      type: Number,
      default: 3
    },
    rows: {
      type: Number,
      default: 3
    }
  },
  data() {
    return {
      winningConfigurations: [],
      noWinner: "No Winner",
      players: [
        {
          symbol: 'X',
          cells: []
        }, {
          symbol: 'O',
          cells: []
        }],
      winner: '', // The winner of the game. Is set to noWinner if all cells are filled.
      turn: 1
    }
  },
  created() {
    this.generatedWinningConfigurations()

  },
  computed: {
    nb_cells() { return this.rows * this.cols },
    currentPlayer() {
      return this.players[this.turn % 2]
    },
    currentPlayerSymbol() {
      return this.currentPlayer.symbol
    }
  },
  methods: {
    reload() {
      // reset the current page
      this.$router.go(this.$router.currentRoute)
    },
    generatedWinningConfigurations() {
      // Generating an array with all available winning configurations
      // columns, rows or diagonals
      // eg row 1, 2, 3 is a winning combination.
      for (let i = 0; i < this.cols; i++) {
        let rowSolution = []
        let colSolution = []

        for (let j = 1; j <= this.rows; j++) {
          rowSolution.push(i * this.cols + j)
          colSolution.push(i + 1 + (j - 1) * this.rows)
        }
        this.winningConfigurations.push(rowSolution)
        this.winningConfigurations.push(colSolution)
      }

      // Diagonals can also win
      let diagSolutionLR = [1]
      let diagSolutionRL = [this.rows]
      for (let i = 1; i < this.cols; i++) {
        diagSolutionLR[i] = diagSolutionLR[i - 1] + this.rows + 1
        diagSolutionRL[i] = diagSolutionRL[i - 1] + this.rows - 1
      }
      this.winningConfigurations.push(diagSolutionLR)
      this.winningConfigurations.push(diagSolutionRL)
    },
    clickedOnCell(event) {
      // If the cell is empty, cell will display the player's symbol
      if (!event.target.innerHTML) {
        event.target.innerHTML = this.currentPlayerSymbol
        this.currentPlayer.cells.push(Number(event.target.getAttribute('data-value')))
        this.checkIfPlayerWon()
        this.turn++
      }
    },
    checkIfPlayerWon() {
      // Check if current player has a winning combination
      let cellsToCheck = this.currentPlayer.cells
      for (let winningConfig of this.winningConfigurations) {
        let won = winningConfig.every(cell => cellsToCheck.includes(cell))
        if (won) this.winner = this.currentPlayer.symbol
      }
      if (this.turn == this.nb_cells) this.winner = this.noWinner
    }
  }
}
</script>

<style>
.info {
  margin-bottom: 3em;
}

.boardgame {
  display: grid;
  width: 60vw;
  margin: 0 auto;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 1fr);
}

.boardgame div {
  border: 1px solid #42b983;
  min-height: 20vh;
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  cursor: pointer;
}
</style>
