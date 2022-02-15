<script setup>
import ColorRow from './ColorRow.vue'
import WhiteImg from '../assets/white-circle.svg'
</script>

<template>
  <table >
    <tbody>
      <tr v-for="(row, idx1) in gameArr" :key="row">
        <td v-for="(col, idx2) in row" :key="col">
          <img :src=getImages(gameArr[idx1][idx2]) />
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  components: { ColorRow },
  props: ['gameArr'],
  methods : {
    getImages(color) {
      console.log(color)
      switch (color) {
        case 'white':
          const whiteUrl = new URL('../assets/white-circle.svg', import.meta.url)
          return whiteUrl;
        case 'black':
          const blackUrl = new URL('../assets/black-circle.svg', import.meta.url)
          return blackUrl
        case 'green':
          const greenUrl = new URL('../assets/green-circle.svg', import.meta.url)
          return greenUrl
        case 'brown':
          const brownUrl = new URL('../assets/brown-circle.svg', import.meta.url)
          return brownUrl
        case 'yellow':
          const yellowUrl = new URL('../assets/yellow-circle.svg', import.meta.url)
          return yellowUrl 
        case 'orange':
          const orangeUrl = new URL('../assets/orange-circle.svg', import.meta.url)
          return orangeUrl 
        case 'purple':
          const purpleUrl = new URL('../assets/purple-circle.svg', import.meta.url)
          return purpleUrl 
      }
    }
  }
}
</script>

<style scoped>
td {
background-color: lightgray;
width: 20px;
height: 20px;
text-align: center;
}

</style>