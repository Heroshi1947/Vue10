<script setup>
import { ref } from 'vue';

const newtask = ref('');
const tasks = ref([]);

// Add a task to the list
const addTask = () => {
    if (newtask.value.trim() != '') {
        tasks.value.push({ text: newtask.value, isEditing: false });
        newtask.value = '';
    }
};

// Remove a task by its index
const removeTask = (index) => {
    tasks.value.splice(index, 1);
};

// Enable task editing
const editTask = (index) => {
    tasks.value[index].isEditing = true;
};

// Save the updated task
const saveTask = (index) => {
    if (tasks.value[index].text.trim() != '') {
        tasks.value[index].isEditing = false;
    }
};
</script>

<template>
    <div class="todo-app">
        <!-- Task input and button to add a new task -->
        <h2>Todo App </h2>
        <div class="task-input">
            <input type="text" v-model="newtask" @keyup.enter="addTask" placeholder="Enter a Task" />
            <button @click="addTask">Add ToDo</button>
        </div>

        <!-- Task list -->
        <ul class="task-list">
            <li v-for="(task, index) in tasks" :key="index" class="task-item">
                <!-- Check if task is in edit mode -->
                <div v-if="task.isEditing">
                    <input type="text" v-model="task.text" />
                    <button class="save" @click="saveTask(index)">Save</button>
                </div>
                <div class="input-field" v-else>
                    <span>

                        {{ task.text }}
                    </span>
                    <button class="edit-button" @click="editTask(index)">Edit</button>
                    <button class="remove-button" @click="removeTask(index)">Delete</button>
                </div>
            </li>
        </ul>
    </div>
</template>



<style scoped>
.todo-app {
    max-width: 400px;
    margin: 50px auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.todo-app h2 {
    display: flex;
    justify-content: center;
}

.app-title {
    font-size: 24px;
    margin-bottom: 20px;
    text-align: center;
    color: #333;
}

.task-input {
    display: flex;
    gap: 10px;
    justify-items: space-between;
}



input {
    flex: 1;
    padding: 8px;
    font-size: 14px;
}

button {

    padding: 8px 12px;
    font-size: 14px;
    background-color: #4caf50;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

button:hover {
    background-color: #45a049;
}

.task-list {
    list-style: none;
    padding: 0;
}

.task-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    margin: 8px 0;
    background-color: #f9f9f9;
    border: 1px solid #ddd;
    border-radius: 4px;
}

.save {
    margin: 5px;
}

.remove-button {
    margin-left: 5px;
    padding: 6px 10px;
    font-size: 12px;
    background-color: #e74c3c;
    color: #fff;
    border: none;
    border-radius: 3px;
    cursor: pointer;
}

.remove-button:hover {
    background-color: #c0392b;
}

.edit-button {
    margin-left: 10px;
    padding: 6px 10px;
    font-size: 12px;
    background-color: #3cd3e7;
    color: #fff;
    border: none;
    border-radius: 3px;
    cursor: pointer;
}

.edit-button:hover {
    background-color: #2b89c0;
}
</style>