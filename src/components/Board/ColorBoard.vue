<template>
  <table class="board">
    <tr v-for="(row, idx1) in gameArr" :key="row">
      <td v-for="(col, idx2) in row" :key="col + idx2">
        <img
          :src="getImages(gameArr[idx1][idx2])"
          :style="{ backgroundColor: checkArr[idx1][idx2] }"
        />
      </td>
    </tr>
  </table>
</template>

<script>
export default {
  components: {},
  props: ['gameArr', 'checkArr'],
  methods: {
    getImages(color) {
      switch (color) {
        case 'white':
          const whiteUrl = new URL('../assets/white-circle.png', import.meta.url)
          return whiteUrl;
        case 'black':
          const blackUrl = new URL('../assets/black-circle.png', import.meta.url)
          return blackUrl
        case 'green':
          const greenUrl = new URL('../assets/green-circle.png', import.meta.url)
          return greenUrl
        case 'brown':
          const brownUrl = new URL('../assets/brown-circle.png', import.meta.url)
          return brownUrl
        case 'yellow':
          const yellowUrl = new URL('../assets/yellow-circle.png', import.meta.url)
          return yellowUrl
        case 'red':
          const orangeUrl = new URL('../assets/red-circle.png', import.meta.url)
          return orangeUrl
        case 'purple':
          const purpleUrl = new URL('../assets/purple-circle.png', import.meta.url)
          return purpleUrl
      }
    }
  }
}
</script>

<style scoped>
td {
  width: 45px;
  height: 45px;
  margin: 0 auto;
  text-align: center;
}

.board {
  margin-left: auto;
  margin-right: auto;
}
</style>