<script setup>
import todoList from './todoList.vue'
import randomQuoteGen from './randomQuoteGen.vue';
import Calculator from './Calculator.vue';
import Accordian from './Accordian.vue';
import formValidation from './formValidation.vue';
import passwordGenerator from './passwordGenerator.vue';
import progressSteps from './progressSteps.vue';
import dadJokes from './dadJokes.vue';
import githubUser from './githubUser.vue';
import wikipedia from './wikipedia.vue';

import { ref } from 'vue';

const currentTab = ref('todoList')

const tabs = {
    todoList,
    randomQuoteGen,
    Calculator,
    Accordian,
    formValidation,
    passwordGenerator,
    progressSteps, dadJokes,
    githubUser,
    wikipedia
}

</script>

<template>
    <div class="nav">
        <br>
        <button @click="currentTab = 'todoList'">Todo List App</button>
        <button @click="currentTab = 'randomQuoteGen'">Quote Generator App</button>
        <button @click="currentTab = 'Calculator'">Calculator App</button>
        <button @click="currentTab = 'Accordian'">Accordian App</button>
        <button @click="currentTab = 'formValidation'">Form Validation App</button>
        <button @click="currentTab = 'passwordGenerator'">Password Generator App</button>
        <button @click="currentTab = 'progressSteps'">Progress Steps App</button>
        <button @click="currentTab = 'dadJokes'">Dad Jokes App</button>
        <button @click="currentTab = 'githubUser'">Search Github App</button>
        <button @click="currentTab = 'wikipedia'">WikiPedia Clone App</button>
        <br>
        <hr>
        <component :is="tabs[currentTab]" />
    </div>

</template>


<style scoped>
button {
    padding: 4px;
    background: #000;
    color: aliceblue;
    margin: 2px;
    cursor: pointer;
}
</style>
