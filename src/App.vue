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
    <ColorBoard :curColor="curColor" :gameArr="gameArr"></ColorBoard>
    <Keyboard @guessed="toto"></Keyboard>
  </main>
</template>

<script>
export default {
  data() {
    return {
      curColor: 'grey',
      curRow: 0,
      curCell: 0,
      gameArr: [['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'],
               ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'],
              ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white'], ['white', 'white', 'white', 'white']]
    }
  },
  methods : {
    toto(curColor) {
      this.curColor = curColor;
      this.gameArr[this.curRow][this.curCell] = curColor
      this.curCell = (this.curCell + 1) % 4
      if (this.curCell == 0) {
        this.curRow = (this.curRow + 1) % 12
      }
    }
  },
}
</script>