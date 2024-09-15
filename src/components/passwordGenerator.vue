<script setup>

import { ref } from 'vue';

const passwordLenth = ref(10)

const includeUppercase = ref(true)

const includeLowercase = ref(true)

const includeSymbols = ref(true)

const includeNumbers = ref(true)

const generatedPassword = ref('')

const copySuccess = ref(false);

const generatePassword = () => {
    const lowercaseChars = includeLowercase.value ? "abcdefghijklmnopqrstuvwxyz" : ''
    const uppercaseChars = includeUppercase.value ? "ABCDEFGHIJKLMNOPQRSTUVWXYZ" : ""
    const numberChars = includeNumbers.value ? "0123456789" : ""
    const symbolChars = includeSymbols.value ? "!@#$%^&*()_+[]{}|;:,.?/~`" : ""
    const allChars = lowercaseChars + uppercaseChars + numberChars + symbolChars
    let password = ''

    for (let i = 0; i < passwordLenth.value; i++) {
        const randomIndex = Math.floor(Math.random() * allChars.length)
        password += allChars[randomIndex]
    }

    generatedPassword.value = password
    copySuccess.value = false;
}


const copyToClipboard = () => {
    navigator.clipboard.writeText(generatedPassword.value).then(() => {
        copySuccess.value = true; // Show success message
        setTimeout(() => {
            copySuccess.value = false; // Hide success message after 3 seconds
        }, 3000);
    });
};

</script>


<template>
    <div class="pass-gen-container">
        <h4 class="pass-gen-title">Password Generator</h4>

        <div class="form-group">
            <label for="length">Password Length :</label>
            <input type="number" id="length" v-model="passwordLenth" min="4" max="20" />
        </div>

        <div class="form-group">
            <label for="includeUppercase">Include Uppercase :</label>
            <input type="checkbox" id="includeUppercase" v-model="includeUppercase">
        </div>

        <div class="form-group">
            <label for="includeLowercase">Include Lowercase :</label>
            <input type="checkbox" id="includeLowercase" v-model="includeLowercase">
        </div>

        <div class="form-group">
            <label for="includeNumbers">Include Numbers :</label>
            <input type="checkbox" id="includeNumbers" v-model="includeNumbers">
        </div>

        <div class="form-group">
            <label for="includeSymbols">Include Symbols :</label>
            <input type="checkbox" id="includeSymbols" v-model="includeSymbols">
        </div>

        <button class="generate-button" @click="generatePassword">Generate Password</button>

        <h4>Your Password:</h4>
        <div class="generated-password" v-if="generatedPassword">
            {{ generatedPassword }}
            <button class="copy-button" @click="copyToClipboard">Copy</button>
        </div>

        <div v-if="copySuccess" class="copy-success">Password copied to clipboard!</div>
    </div>
</template>

<style scoped>
/* Container Styling */
.pass-gen-container {
    max-width: 350px;
    margin: 25px auto;
    padding: 30px;
    background-color: #fff;
    border-radius: 10px;
    box-shadow: 0 8px 15px rgba(0, 0, 0, 0.1);
    text-align: center;
    font-family: 'Arial', sans-serif;
}

/* Title Styling */
.pass-gen-title {
    font-size: 25px;
    font-weight: bold;
    color: #2c3e50;
    margin-bottom: 25px;
}

/* Input Fields and Checkbox Styling */
.form-group {
    margin-bottom: 20px;
    text-align: left;
}

label {
    font-size: 16px;
    color: #2c3e50;
}

input[type="number"] {
    width: 95%;
    padding: 10px;
    margin-top: 5px;
    font-size: 16px;
    border: 1px solid #ccc;
    border-radius: 6px;
    transition: border-color 0.3s ease;
}

input[type="checkbox"] {
    margin-left: 10px;
    transform: scale(1.2);
    cursor: pointer;
}

input:focus {
    border-color: #3498db;
    outline: none;
    box-shadow: 0 0 10px rgba(52, 152, 219, 0.2);
}

/* Generate Button */
.generate-button {
    width: 100%;
    padding: 10px;
    font-size: 18px;
    background-color: #e74c3c;
    color: #fff;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    transition: background-color 0.3s, transform 0.2s;
}

.generate-button:hover {
    background-color: #bc2b1b;
    transform: scale(1.01);
}




.generated-password {
    display: flex;
    justify-content: space-around;
    margin-top: 10px;
    padding: 12px;
    border: 1px solid #ddd;
    border-radius: 6px;
    background-color: #dce8ff;
    color: #21354a;
    font-size: 18px;
    /* font-weight: bold; */
    word-wrap: break-word;
}

.copy-button {
    padding: 5px;
    font-size: 15px;
    color: rgb(13, 13, 203);
    border: none;
    border-radius: 8px;
    cursor: pointer;
    transition: background-color 0.3s, transform 0.2s;
}

.copy-success {
    margin: 5px;
    color: #3498db;
}
</style>
