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
    <span>Orange : Couleur mal placé</span>
    <br>
    <span>Vert : Couleur bien placé</span>
    <ColorBoard :gameArr="gameArr" :checkArr="checkArr"></ColorBoard>
    <Keyboard @guessed="updateGameArr"></Keyboard>
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
  console.log(won)
  return won == 4
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
              ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white']],
      checkArr: [['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'],
               ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'],
              ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white']],
      
    }
  },
  methods : {
    updateGameArr(curColor) {
      this.gameArr[this.curRow][this.curCell] = curColor
      this.curCell = (this.curCell + 1) % 4
      if (this.curCell == 0) {
        if (check(this.gameArr[this.curRow], this.checkArr[this.curRow], this.secret)) {
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