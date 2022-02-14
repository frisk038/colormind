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
    <ColorBoard></ColorBoard>
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
    }
  },
  methods : {
    toto(curColor) {
      this.curColor = curColor;
      ColorBoard.methods.updateRow(this.curColor, this.curRow, this.curCell);
    }
  },
}
</script>