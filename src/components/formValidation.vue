<script setup>
import { ref, computed } from 'vue';

const formData = ref({
    name: '',
    email: '',
    password: ''
})

const isNameValid = computed(() => formData.value.name.trim() != '')
const isPasswordValid = computed(() => formData.value.password.length >= '5')
const isEmailValid = computed(() => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(formData.value.email))
const isFormValid = computed(() => isEmailValid.value && isNameValid.value && isPasswordValid.value)

const submitform = () => {
    if (isFormValid.value) {
        alert(" Registration was successful ! ");
        formData.value = { name: '', email: '', password: '' };
    } else {
        alert(" Invalid form Data! ")
    }
}

</script>

<template>
    <form @submit.prevent="submitform" class="custom-form">
        <h2>Form Validation</h2>
        <div class="form-group">
            <label for="name">Name:</label>
            <input type="text" v-model="formData.name" id="name">
            <span v-if="!isNameValid" class="error">Name is Required</span>
        </div>

        <div class="form-group">
            <label for="Email">Email:</label>
            <input type="text" v-model="formData.email" id="Email">
            <span v-if="!isEmailValid" class="error">Please enter a valid Email Id</span>
        </div>

        <div class="form-group">
            <label for="Password">Password:</label>
            <input type="text" v-model="formData.password" id="Password">
            <span v-if="!isPasswordValid" class="error">Password must be 5 characters long</span>
        </div>
        <button type="submit" :disabled="!isFormValid" class="submit-button">Submit</button>
    </form>
</template>

<style scoped>
.custom-form {
    padding: 25px 75px;
    border: 2px solid #ccc;
    border-radius: 15px;
    max-width: 400px;
    margin: 50px auto;
}

.form-group {
    margin-bottom: 20px;
}

h2 {
    display: flex;
    justify-content: center;
}

label {
    display: block;
    font-weight: bold;
    margin-bottom: 5px;
}

input {
    width: 100%;
    padding: 10px;
    font-size: 16px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

.error {
    color: #d21d09;
    font-size: 15px;
    margin-top: 5px;
}

.submit-button {
    margin: 0 40%;
    padding: 10px 15px;
    font-size: 16px;
    background-color: #42a0de;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

.submit-button:disabled {
    background-color: #bdc3c7;
    cursor: not-allowed;
}
</style>
