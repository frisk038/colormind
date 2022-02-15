<script setup>
import ColorBoard from './components/Board/ColorBoard.vue';
import Header from './components/Header/Header.vue';
import Keyboard from './components/Keyboard.vue';
</script>

<template>
  <header>
    <Header></Header>
  </header>
  <main>
    <h1 v-if="won">Bravo</h1>
    <ColorBoard :gameArr="gameArr"></ColorBoard>
    <Keyboard @guessed="updateGameArr"></Keyboard>
  </main>
</template>

<script>
function getSecret() {
  var colors = ['black', 'green', 'brown', 'yellow', 'orange', 'purple']
  return [colors[Math.floor(Math.random() * colors.length)],
          colors[Math.floor(Math.random() * colors.length)],
          colors[Math.floor(Math.random() * colors.length)],
          colors[Math.floor(Math.random() * colors.length)]]
}

function arrayEquals(a, b) {
  return a.every((val, index) => val === b[index]);
}

export default {
  data() {
    return {
      won : false,
      secret : [],
      curRow: 0,
      curCell: 0,
      gameArr: [['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'],
               ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'],
              ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white']]
    }
  },
  methods : {
    updateGameArr(curColor) {
      this.gameArr[this.curRow][this.curCell] = curColor
      this.curCell = (this.curCell + 1) % 4
      if (this.curCell == 0) {
        if (arrayEquals(this.gameArr[this.curRow], this.secret)) {
          this.won = true;
        }

        this.curRow = (this.curRow + 1) % 12
      }
    }
  },
  created(){
      this.secret = getSecret()
      console.log(this.secret)
  },
}
</script>