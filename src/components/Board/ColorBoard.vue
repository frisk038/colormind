<script setup>
import ColorRow from './ColorRow.vue'
</script>

<template>
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
  </table>
</template>

<script>
export default {
  components: { ColorRow },
  methods : {
    updateRow(curColor, curRow, curCell) {
      console.log(curColor, curRow, curCell);
    }
  }
}
</script>

<style>

</style>