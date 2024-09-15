<script setup>
import { ref, onMounted } from 'vue';

const quotes = ref([
    {
        text: "Success is not the key to happiness. Happiness is the key to success.",
        author: "Albert Schweitzer",
    },
    {
        text: "Don't watch the clock; do what it does. Keep going.",
        author: "Sam Levenson",
    },
    {
        text: "The best way to predict the future is to invent it.",
        author: "Alan Kay",
    },
    {
        text: "You miss 100% of the shots you don't take.",
        author: "Wayne Gretzky",
    },
    {
        text: "The only limit to our realization of tomorrow is our doubts of today.",
        author: "Franklin D. Roosevelt",
    },
    {
        text: "The harder I work, the luckier I get.",
        author: "Gary Player",
    },
    {
        text: "It does not matter how slowly you go as long as you do not stop.",
        author: "Confucius",
    },
    {
        text: "Strive not to be successful, but rather to be of value.",
        author: "Albert Einstein",
    },
    {
        text: "The only place where success comes before work is in the dictionary.",
        author: "Vidal Sassoon",
    },
    {
        text: "Success usually comes to those who are too busy to be looking for it.",
        author: "Henry David Thoreau",
    },

])

const currentQuote = ref({ text: '', author: '' })

const getRandomQuote = () => {
    const randomIndex = Math.floor(Math.random() * quotes.value.length)
    currentQuote.value = quotes.value[randomIndex]
}

onMounted(getRandomQuote)

</script>

<template>
    <div class="quote-generator">
        <h1 class="app-title">Quote Of the Day</h1>
        <blockquote class="quote-container">
            <p>{{ currentQuote.text }}</p>
            <cite>{{ currentQuote.author }}</cite>
        </blockquote>
        <button @click="getRandomQuote" class="quote-button">More</button>
    </div>

</template>

<style scoped>
.quote-generator {
    max-width: 400px;
    margin: 50px auto;
    padding: 20px;
    text-align: center;
    border: 1px solid #ccc;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.app-title {
    font-size: 24px;
    margin-bottom: 20px;
    color: #333;
}

.quote-container {
    background-color: #f9f9f9;
    padding: 20px;
    border-radius: 8px;
    border: 1px solid #ddd;
    margin-bottom: 20px;
}

p {
    font-size: 18px;
    margin-bottom: 10px;
}

cite {
    font-style: normal;
    color: #c61717;
}

.quote-button {
    padding: 10px 20px;
    font-size: 16px;
    background-color: #3498db;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

.quote-button:hover {
    background-color: #2980b9;
}
</style>