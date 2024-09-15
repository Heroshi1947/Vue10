<script setup>
import { ref } from 'vue';
import axios from 'axios';

const joke = ref(null)

const fetchJoke = async () => {
    try {
        const response = await axios.get('https://icanhazdadjoke.com/', {
            headers: { Accept: 'application/json' }
        })
        joke.value = response.data.joke
    } catch (error) {
        console.log("Error in fetching the jokes! ", error)
    }
}


</script>

<template>
    <div class="jokes-container">
        <h2 class="joke-title">Dad Jokes</h2>
        <button @click="fetchJoke" class="get-joke-button">Get Jokes</button>
        <div class="dad-joke" v-if="joke">{{ joke }}</div>
    </div>
</template>

<style scoped>
.jokes-container {
    display: flex;
    flex-direction: column;
    max-width: 600px;
    margin: 50px auto;
}

.joke-title {
    display: flex;
    justify-content: center;
    font-size: 24px;
    color: #333;
    margin-bottom: 20px;
}

.get-joke-button {
    margin: 0 auto;
    width: 50%;
    padding: 10px 15px;
    font-size: 16px;
    background-color: #1c50aa;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

.get-joke-button:hover {
    background-color: #201c9f;
}

.dad-joke {
    text-align: center;
    border: 1px solid #ddd;
    border-radius: 4px;
    padding: 15px;
    margin-top: 20px;
    background-color: #f9f9f9;
    color: #333;
}
</style>
