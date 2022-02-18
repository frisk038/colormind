<template>
    <div @click.self="$emit('closeHelp')" class="modal-backdrop">
        <div class="modal">
            <section class="modal-body">
                <h1>Règles 🥸</h1>
                <span>
                    <div>
                        Le but du jeu est de deviner en un minimum de coup
                        <br />la combinaison du jour. Et pour ceci vous avez
                        <br />8 petits tours !
                        <br />
                        <br />
                    </div>
                    <div>
                        <img src="./assets/example.png" class="exampleImg" />
                        <br />Si la combinaison contient une ou plusieurs
                        <br />couleur mal placé elles auront un fond orange 🟧.
                        <br />Et verte pour une couleur bien placée 🟩.
                    </div>
                    <br />Bonne chance 🤞 !
                    <div class="closeDiv">
                        <button @click="$emit('closeHelp')">C'est parti !</button>
                    </div>
                </span>
            </section>
        </div>
    </div>
</template>

<script>
export default {
    emits: ['closeHelp'],
    props: ['helpRequired'],
    data() {
        return {
        }
    },
    methods: {
        close() {
            this.helpRequired = false
        },
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

.exampleImg {
    width: 15em;
}

.closeDiv {
    width: 100%;
    text-align: right;
}
</style>
