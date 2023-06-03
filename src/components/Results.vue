<template>
    <div class="resultsContainer">
        <p>Your score - {{ this.score }}</p>
        <p class="yourScore">{{ rank }}</p>
    </div>
</template>

<script>
export default {
    props: ["score"],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if (this.score < 250) {
            this.rank = "ninja reflexes"
        }else if (this.score < 500) {
            this.rank = "not bad"
        }else{
            this.rank = "turtle pace lol..."
        }
    }
}
</script>

<style scoped>
.resultsContainer {
    margin-top: 20px;
    padding: 10px;
    background-color: aqua;
    border: 1px solid black;
    text-align: center;
    display: flex;
    flex-direction: column;
    border-radius: 10px;
}

p{
    color: black;
}
.yourScore {
    font-size: 18px;
    color: darkviolet;
}
</style>