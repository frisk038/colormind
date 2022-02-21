<script setup>
import ColorBoard from './components/Board/ColorBoard.vue';
import Header from './components/Header/Header.vue';
import Keyboard from './components/Keyboard.vue';
import WinPopup from './components/WinPopup.vue'
</script>

<template>
  <header>
    <Header></Header>
    <WinPopup v-if="gameState != 0" :gameResume="gameResume" :gameState="gameState"></WinPopup>
  </header>
  <main>
    <ColorBoard :gameArr="gameArr" :checkArr="checkArr"></ColorBoard>
    <Keyboard @guessed="updateGameArr" @clear="clearRow" @check="checkRow"></Keyboard>
  </main>
  {{ secret }}
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
      gameState: 0,
      secret: [],
      curRow: 0,
      curCell: 0,
      isPopupVisible: false,
      gameArr: [['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'],
      ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white']],
      checkArr: [['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'],
      ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white']],
      gameResume: [],
    }
  },
  methods: {
    updateGameArr(curColor) {
      if (this.curCell < 4 && this.gameState == 0) {
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
      console.log(this.secret)
      if (this.curCell == 4 && this.gameState == 0) {
        if (check(this.gameArr[this.curRow], this.checkArr[this.curRow], this.secret)) {
          this.gameState = 1;
          this.computeClipBoard()
          this.showPopup()
          return
        }
        if (this.curRow < 7) {
          this.curRow++
          this.curCell = 0
        }
        else {
          this.gameState = -1
          this.computeClipBoard()
          this.showPopup()
        }
      }
    },
    showPopup() {
      this.isPopupVisible = true;
    },
    computeClipBoard() {
      for (let irow = 0; irow <= this.curRow; irow++) {
        var row = []
        for (let icell = 0; icell < this.checkArr[irow].length; icell++) {
          const element = this.checkArr[irow][icell];
          switch (element) {
            case 'orange':
              row.push('🟠')
              break;
            case 'green':
              row.push('🟢')
              break;
            case 'white':
              row.push('⚪️')
            default:
              break;
          }
        }
        this.gameResume.push(row)
      }
    },
  },
  async beforeMount() {
    try {
      let response = await fetch("https://bamboocolor.herokuapp.com/combination");
      console.log("response=", response.json().status);
      var combiJs = await response.json().result;
      var combiObj = JSON.parse(combiJs);
      this.secret = combiObj.combi
    } catch (error) {
      console.log(error);
    }
  },
}
</script>