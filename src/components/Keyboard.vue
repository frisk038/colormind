<template>
    <table class="color">
        <td>
            <button class="black" @click="$emit('guessed', 'black')" />
        </td>
        <td>
            <button class="green" @click="$emit('guessed', 'green')" />
        </td>
        <td>
            <button class="brown" @click="$emit('guessed', 'brown')" />
        </td>
        <td>
            <button class="yellow" @click="$emit('guessed', 'yellow')" />
        </td>
        <td>
            <button class="red" @click="$emit('guessed', 'red')" />
        </td>
        <td>
            <button class="purple" @click="$emit('guessed', 'purple')" />
        </td>
    </table>
    <table class="system">
        <td>
            <button class="clear" @click="$emit('clear')" />
        </td>
        <td>
            <button class="check" @click="$emit('check')" />
        </td>
    </table>
</template>

<script>
export default {
    emits: ['guessed', 'clear', 'check']
}
</script>

<style scoped>
.black {
    background: url("./assets/bambou/black.png") no-repeat;
    background-size: cover;
    width: 50px;
    height: 50px;
    border-radius: 10px;
}
.green {
    background: url("./assets/bambou/green2.png") no-repeat;
    background-size: cover;
    width: 50px;
    height: 50px;
    border-radius: 10px;
}
.brown {
    background: url("./assets/bambou/brown.png") no-repeat;
    background-size: cover;
    width: 50px;
    height: 50px;
    border-radius: 10px;
}
.yellow {
    background: url("./assets/bambou/yellow.png") no-repeat;
    background-size: cover;
    width: 50px;
    height: 50px;
    border-radius: 10px;
}
.red {
    background: url("./assets/bambou/red.png") no-repeat;
    background-size: cover;
    width: 50px;
    height: 50px;
    border-radius: 10px;
}
.purple {
    background: url("./assets/bambou/purple.png") no-repeat;
    background-size: cover;
    width: 50px;
    height: 50px;
    border-radius: 10px;
}
.check {
    background: url("./assets/check.png") no-repeat;
    background-size: cover;
    width: 50px;
    height: 50px;
    border-radius: 10px;
}
.clear {
    background: url("./assets/cancel.png") no-repeat;
    background-size: cover;
    width: 50px;
    height: 50px;
    border-radius: 10px;
}
.color {
    width: 100%;
    margin: 0 auto;
    text-align: center;
}
.system {
    width: 70%;
    margin: 0 auto;
    text-align: center;
}
</style>