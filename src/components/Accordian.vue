<script setup>
import { ref } from 'vue';

const items = ref([
    {
        title: "What is HTML?",
        content: "HTML stands for HyperText Markup Language, used to structure content on the web.",
        open: false,
    },
    {
        title: "What is JavaScript?",
        content: "JavaScript is a scripting language used to create dynamic content on websites.",
        open: false,
    },
    {
        title: "What is Python?",
        content: "Python is a high-level programming language known for its simplicity and versatility.",
        open: false,
    },
    {
        title: "What is React?",
        content: "React is a JavaScript library used for building user interfaces, mainly for web applications.",
        open: false,
    },
    {
        title: "What is Vue.js?",
        content: "Vue.js is a progressive JavaScript framework used for building user interfaces and single-page applications.",
        open: false,
    },
    {
        title: "What is Node.js?",
        content: "Node.js is a runtime environment that allows JavaScript to be executed server-side.",
        open: false,
    },
    {
        title: "What is SQL?",
        content: "SQL stands for Structured Query Language, used for managing and querying relational databases.",
        open: false,
    },


])

const toggleAccordian = (index) => {
    items.value = items.value.map((item, i) => ({
        ...item,
        open: i === index ? !item.open : false
    }))
}
</script>

<template>

    <div class="accordion-container">
        <div class="accordion" v-for="(item, index) in items" :key="index">
            <div class="accordion-header" @click="toggleAccordian(index)">
                {{ item.title }}
                <span class="arrow-icon">{{ item.open ? "▼" : "▶" }}</span>
            </div>
            <div v-show="item.open" class="accordion-content">{{ item.content }}</div>
        </div>

    </div>

</template>

<style scoped>
.accordion-container {
    max-width: 600px;
    margin: 50px auto;
}

.accordion {
    border: 1px solid #ddd;
    border-radius: 4px;
    overflow: hidden;
    margin-bottom: 10px;
}

.accordion-header {
    background-color: #1fb2fc;
    color: #fff;
    padding: 15px;
    cursor: pointer;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.arrow-icon {
    font-size: 20px;
}

.accordion-content {
    padding: 15px;
    display: none;
    border-top: 2px solid #ddd;
    background-color: #fee8e8;
    color: #333;
}

.accordion-content[style] {
    display: block;
}
</style>