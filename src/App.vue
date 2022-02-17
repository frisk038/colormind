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
    <h1 v-if="gameState == 1">Bravo</h1>
    <h1 v-if="gameState == -1">Dommage</h1>
    <ColorBoard :gameArr="gameArr" :checkArr="checkArr"></ColorBoard>
    <Keyboard @guessed="updateGameArr" @clear="clearRow" @check="checkRow"></Keyboard>
  </main>
</template>

<script>
function getSecret() {
  var colors = ['black', 'green', 'brown', 'yellow', 'red', 'purple']
  return [colors[Math.floor(Math.random() * colors.length)],
          colors[Math.floor(Math.random() * colors.length)],
          colors[Math.floor(Math.random() * colors.length)],
          colors[Math.floor(Math.random() * colors.length)]]
}

function check(gameArr, checkArr, secretArr) {
  var won = 0
  for (let index = 0; index < gameArr.length; index++) {
    if (secretArr.includes(gameArr[index])) {
      checkArr[index] = "orange"
    }
    if (gameArr[index] == secretArr[index]) {
      checkArr[index] = "green"
      won++
    } 
  }
  return won == 4
}

export default {
  data() {
    return {
      gameState : 0,
      secret : [],
      curRow: 0,
      curCell: 0,
      gameArr: [['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'],
               ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white']],
      checkArr: [['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'],
               ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white']],
    }
  },
  methods : {
    updateGameArr(curColor) {
      if (this.curCell < 4) {
        this.gameArr[this.curRow][this.curCell] = curColor
        this.curCell++
      }
    },
    clearRow() {
      for (let index = 0; index < this.gameArr[this.curRow].length; index++) {
        this.gameArr[this.curRow][index] = 'white';
      }
      this.curCell = 0
    },
    checkRow() {
      if (this.curCell == 4) {
        if (check(this.gameArr[this.curRow], this.checkArr[this.curRow], this.secret)) {
          this.gameState = 1;
          return
        }
        if (this.curRow < 8) {
          this.curRow++
          this.curCell = 0
        }
        else {
          this.gameState = -1
        }   
      }
    }
  },
  created(){
      this.secret = getSecret()
      console.log(this.secret)
  },
}
</script>