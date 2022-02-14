<template>
    <tr>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td class="rowStats"> <RowStats></RowStats></td>
    </tr> 
</template>

<script>
import RowStats from "./RowStats.vue";
export default {
    components: { RowStats }
}
</script>

<style scoped>
td {
background-color: lightgray;
width: 20px;
height: 20px;
text-align: center;
}
.rowStats{
    background-color: white;
    width: auto;
}
</style>