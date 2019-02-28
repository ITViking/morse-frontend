<template>
    <main>
        <h1>Morse</h1>
        <h2>Bringing yet another oldschool into the 21st century</h2>
        <div class="messaging-container">
            <div v-for="(item) in data" :key="item.id">
                <p class="ip">{{ item.ip }}</p>
                <p class="message">{{ item.message }}</p>
            </div>
        </div>
    </main>
</template>

<script>
    import axios from 'axios'

    export default {
        data() {
            return {
                 messages: "Hej",
                 data: null,
            };
        },
        async mounted() {
            await axios.get('http://localhost:5000').then(response => {
                this.data = response.data;
            });
        },
    }
</script>

<style lang="css">
    body {
        background: lightblue;
    }

    h1, h2 {
        text-align: center;
    }

    .messaging-container {
        overflow-y: scroll;
        height: 70vh;
        width: 90vw;
        background-color: whitesmoke;
        margin: 0 auto;
        border-radius: 10px;
        padding: 1em;
    }

    .ip {
        margin-bottom: 2px;
        font-size: 0.9em;
    }

    .message {
        margin-top: 2px;
        font-size: 1.2em;
        font-weight:900;
    }

</style>