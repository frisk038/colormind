<template>
    <table class="headTab">
        <td>
            <button class="leaderboard" />
        </td>
        <td>
            <img src="../assets/panda1.png" class="logo" />
        </td>
        <td>
            <button class="help" />
        </td>
    </table>
</template>

<script>
export default {

}
</script>

<style scoped>
.logo {
    width: 4em;
}

.help {
    background: url("../assets/leaderboard.png") no-repeat;
    background-size: cover;
    width: 50px;
    height: 50px;
    border-radius: 10px;
}
.leaderboard {
    background: url("../assets/help.png") no-repeat;
    background-size: cover;
    width: 50px;
    height: 50px;
    border-radius: 10px;
}

.headTab {
    margin: 0 auto;
    text-align: center;
    width: 25em;
}
</style>