<template>
    <table class="headTab">
        <td>
            <button class="leaderboard" v-on:click="getData" />
        </td>
        <td>
            <img src="../assets/panda1.png" class="logo" />
        </td>
        <td>
            <button class="help" v-on:click="helpNeeded = !helpNeeded" />
        </td>
    </table>
    <HelpPopup v-show="helpNeeded" @closeHelp="closeHelp"></HelpPopup>
    {{ combi }}
</template>

<script>
import HelpPopup from "../HelpPopup.vue";
export default {
    components: { HelpPopup },
    data() {
        return {
            helpNeeded: true,
            combi: ""
        }
    },
    methods: {
        closeHelp() {
            this.helpNeeded = false
        },
        async getData() {
            try {
                let response = await fetch("https://bamboocolor.herokuapp.com/combination");
                this.combi = await response.json();
            } catch (error) {
                console.log(error);
            }
        },
    },
}
</script>

<style scoped>
.logo {
    width: 4em;
}

.help {
    background: url("../assets/help.png") no-repeat;
    background-size: cover;
    width: 50px;
    height: 50px;
    border-radius: 10px;
}
.leaderboard {
    background: url("../assets/leaderboard.png") no-repeat;
    background-size: cover;
    width: 50px;
    height: 50px;
    border-radius: 10px;
}

.headTab {
    margin: 0 auto;
    text-align: center;
    width: 20em;
}
</style>