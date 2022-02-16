<template>
      <button class="black"  @click="$emit('guessed', 'black')" />
      <button class="green"  @click="$emit('guessed', 'green')" />
      <button class="brown"  @click="$emit('guessed', 'brown')" />
      <button class="yellow" @click="$emit('guessed', 'yellow')" />
      <button class="red" @click="$emit('guessed', 'red')" />
      <button class="purple" @click="$emit('guessed', 'purple')" />
</template>

<script>
export default {
    emits: ['guessed']
}
</script>

<style>
.black {
    background: url('./assets/black-circle.svg') no-repeat;
    width:50px;height:50px;
}
.green {
    background: url('./assets/green-circle.svg') no-repeat;
    width:50px;height:50px;
}
.brown {
    background: url('./assets/brown-circle.svg') no-repeat;
    width:50px;height:50px;
}
.yellow {
    background: url('./assets/yellow-circle.svg') no-repeat;
    width:50px;height:50px;
}
.red {
    background: url('./assets/red-circle.svg') no-repeat;
    width:50px;height:50px;
}
.purple {
    background: url('./assets/purple-circle.svg') no-repeat;
    width:50px;height:50px;
}
</style>