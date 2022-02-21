<template>
    <div class="modal-backdrop">
        <div class="modal">
            <section class="modal-body">
                <div v-if="gameState == 1">
                    <h1>Félicitations 🎉</h1>
                    <span>Bravo, tu as gagné. Reviens demain pour un nouveau défi.</span>
                </div>
                <div v-else>
                    <h1>Perdu 🥺</h1>
                    <span>Arf, dommage! Retente ta chance demain!</span>
                </div>

                <div class="share">
                    <button v-on:click="generateClipboard">Partage ta partie</button>
                    <table class="shareTab">
                        <tr v-for="(row, idx1) in gameResume" :key="row">
                            <td
                                v-for="(col, idx2) in row"
                                :key="col + idx2"
                            >{{ gameResume[idx1][idx2] }}</td>
                        </tr>
                    </table>
                </div>
            </section>
        </div>
    </div>
</template>

<script>
export default {
    props: ['gameResume', 'curRow', 'gameState', 'secret'],
    data() {
        return {
        }
    },
    methods: {
        close() {
            this.$emit('close');
        },
        generateClipboard() {
            var text = "Bamboo Color\n\n"
            for (let iRow = 0; iRow < this.gameResume.length; iRow++) {
                const row = this.gameResume[iRow];
                for (let iCol = 0; iCol < row.length; iCol++) {
                    text += row[iCol];
                }
                text += '\n'
            }
            text += '\nhttps://bambo-color.netlify.app'
            this.copyToClipboard(text)
        },
        async copyToClipboard(mytext) {
            try {
                await navigator.clipboard.writeText(mytext);
                alert("C'est copié");
            } catch ($e) {
                alert('Oups y a une erreur');
            }
        }
    },
};
</script>

 <style scoped>
.modal-backdrop {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: rgba(0, 0, 0, 0.6);
    display: flex;
    justify-content: center;
    align-items: center;
}

.modal {
    background: #474747;
    box-shadow: 2px 2px 20px 1px;
}

.modal-body {
    position: relative;
    padding: 20px 5px;
    color: #ffffff;
}

.share {
    margin: 0 auto;
    text-align: center;
}

.shareTab {
    margin: 0 auto;
    text-align: center;
}
</style>
