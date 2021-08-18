<template>
  <div class="home">
    <h1>Tit tac toe</h1>
    <div class="input-names" v-if="!gameStarted">
      <div>
        Enter Player 1 name:
        <input type="text" v-model="player1" style="margin: 10px" />
      </div>
      <div>
        Enter Player 2 name:
        <input type="text" v-model="player2" style="margin: 10px" />
      </div>
      <button @click="startGame" style="margin: 10px">Start Game</button>
    </div>
    <div v-else-if="gameDecided && gameStarted">
      The Winner is {{ winnersName }} !!

      <div class="restart-game">
        <button @click="restartGame" style="margin: 10px">Restart Game</button>
      </div>
    </div>
    <div v-else>
      <div class="notice-board">Player 1 : X Player 2: O</div>
      <div class="restart-game">
        <button @click="restartGame">Restart Game</button>
      </div>
      <div class="name-current-player">
        Current Player: {{ currentPlayerName }}
      </div>

      <div class="center-board">
        <div class="board">
          <div class="row">
            <div @click="setPrevious()">
              <button
                @click="square1 = playerKey"
                style="height: 100px; width: 250px; margin: 10px"
              >
                {{ square1 }}
              </button>
            </div>
            <div @click="setPrevious()">
              <button
                @click="square2 = playerKey"
                style="height: 100px; width: 250px; margin: 10px"
              >
                {{ square2 }}
              </button>
            </div>
            <div @click="setPrevious()">
              <button
                @click="square3 = playerKey"
                style="height: 100px; width: 250px; margin: 10px"
              >
                {{ square3 }}
              </button>
            </div>
          </div>
        </div>
        <div class="board">
          <div class="row">
            <div @click="setPrevious()">
              <button
                @click="square4 = playerKey"
                style="height: 100px; width: 250px; margin: 10px"
              >
                {{ square4 }}
              </button>
            </div>
            <div @click="setPrevious()">
              <button
                @click="square5 = playerKey"
                style="height: 100px; width: 250px; margin: 10px"
              >
                {{ square5 }}
              </button>
            </div>
            <div @click="setPrevious()">
              <button
                @click="square6 = playerKey"
                style="height: 100px; width: 250px; margin: 10px"
              >
                {{ square6 }}
              </button>
            </div>
          </div>
        </div>
        <div class="board">
          <div class="row">
            <div @click="setPrevious()">
              <button
                @click="square7 = playerKey"
                style="height: 100px; width: 250px; margin: 10px"
              >
                {{ square7 }}
              </button>
            </div>
            <div @click="setPrevious()">
              <button
                @click="square8 = playerKey"
                style="height: 100px; width: 250px; margin: 10px"
              >
                {{ square8 }}
              </button>
            </div>
            <div @click="setPrevious()">
              <button
                @click="square9 = playerKey"
                style="height: 100px; width: 250px; margin: 10px"
              >
                {{ square9 }}
              </button>
            </div>
          </div>
        </div>
        <button @click="decideWinner">Who Won?</button>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from "vue";
// @ is an alias to /src

export default Vue.extend({
  name: "Home",
  components: {},
  data() {
    return {
      square1: "",
      square2: "",
      square3: "",
      square4: "",
      square5: "",
      square6: "",
      square7: "",
      square8: "",
      square9: "",
      player1: "",
      player2: "",
      gameStarted: false,
      gameDecided: false,
      winner: "",
      previous: "",
    };
  },

  computed: {
    currentPlayerName() {
      return this.playerKey == "X" ? this.player1 : this.player2;
    },
    winnersName() {
      return this.winner == "Player1" ? this.player1 : this.player2;
    },
    playerKey() {
      return this.previous == "X" ? "O" : "X";
    },
  },

  methods: {
    setPrevious() {
      this.previous = this.playerKey;
    },
    decideWinner() {
      this.gameDecided = true;

      // horizontal win for  O
      if (((this.square1 == this.square2) == this.square3) == "O") {
        return (this.winner = "Player2");
      }
      if (((this.square4 == this.square5) == this.square6) == "O") {
        return (this.winner = "Player2");
      }
      if (((this.square7 == this.square8) == this.square9) == "O") {
        return (this.winner = "Player2");
      }
      // vertical win for O
      if (((this.square1 == this.square4) == this.square7) == "O") {
        return (this.winner = "Player2");
      }
      if (((this.square2 == this.square5) == this.square8) == "O") {
        return (this.winner = "Player2");
      }
      if (((this.square3 == this.square6) == this.square9) == "O") {
        return (this.winner = "Player2");
      }
      // diaoginal win for O
      if (((this.square1 == this.square5) == this.square9) == "O") {
        return (this.winner = "Player2");
      }
      if (((this.square3 == this.square5) == this.square7) == "O") {
        return (this.winner = "Player2");
      }

      // horizontal win for  X
      if (((this.square1 == this.square2) == this.square3) == "X") {
        return (this.winner = "Player1");
      }
      if (((this.square4 == this.square5) == this.square6) == "X") {
        return (this.winner = "Player1");
      }
      if (((this.square7 == this.square8) == this.square9) == "X") {
        return (this.winner = "Player1");
      }
      // vertical win for X
      if (((this.square1 == this.square4) == this.square7) == "X") {
        return (this.winner = "Player1");
      }
      if (((this.square2 == this.square5) == this.square8) == "X") {
        return (this.winner = "Player1");
      }
      if (((this.square3 == this.square6) == this.square9) == "X") {
        return (this.winner = "Player1");
      }
      // diaoginal win for X
      if (((this.square1 == this.square5) == this.square9) == "X") {
        return (this.winner = "Player1");
      }
      if (((this.square3 == this.square5) == this.square7) == "X") {
        return (this.winner = "Player1");
      }
    },
    restartGame() {
      this.gameStarted = false;
      location.reload();
    },
    startGame() {
      this.gameStarted = true;
      this.playerKey = "X";
    },
  },
});
</script>

<style scoped>
.center-board {
}
.board {
  display: flex;
}
.row {
  display: flex;
  width: 500px;
}

.column {
  height: 100px;
  width: 250px;
  margin: 10px;
  background-color: #ffff;
  border: 2px solid gray;
}
</style>
