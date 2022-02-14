<script setup>
import ColorRow from './ColorRow.vue'
</script>

<template>
  <!-- Pass binding to sub element
    <table>
    <ColorRow></ColorRow>
    <ColorRow></ColorRow>
    <ColorRow></ColorRow>
    <ColorRow></ColorRow>
    <ColorRow></ColorRow>
    <ColorRow></ColorRow>
    <ColorRow></ColorRow>
    <ColorRow></ColorRow>
    <ColorRow></ColorRow>
    <ColorRow></ColorRow>
    <ColorRow></ColorRow>
    <ColorRow></ColorRow>
  </table> -->
  <table >
    <tbody>
      <tr v-for="(row, idx1) in gameArr" :key="row">
        <td v-for="(col, idx2) in row" :key="col">
          <img v-bind:src="'src/components/assets/' +gameArr[idx1][idx2] + '-circle.svg'"/>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  components: { ColorRow },
  props: ['curColor', 'gameArr'],
  methods : {
    updateRow(curColor, curRow, curCell) {
      console.log(curColor, curRow, curCell);
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