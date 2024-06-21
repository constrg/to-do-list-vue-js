<script setup>
import { ref } from 'vue'

const newTask = ref('')
const tasks = ref([])

const addTask = () => {
    if (newTask.value.trim() !== '') {
        tasks.value.push(newTask.value)
        newTask.value = ''
    }
}

const removeTask = (index) => {
    tasks.value.splice(index, 1)
}

const clearAllTask = () => {
    tasks.value = []
}

</script>
<template>
    <div class="todo-app">
        <h1>To-do List {Vue}</h1>
        <div class="task-input">
            <input v-model="newTask" v-on:keyup.enter="addTask" placeholder="Add new Todo">
            <button v-on:click="addTask" class="add-task-btn">Add To Do</button>
        </div>

        <ul class="task-list">
            <h2>Task List</h2>
            <li v-for="(task, index) in tasks" v-bind:key="index" v-bind:style="{'text-decoration': isCompleted ? 'line-through' : 'none'}" class="task-item">
                {{ task }}
            <button v-on:click="removeTask(index)" class="remove-task">Remove Task</button>
            </li>

            <div class="clear-all-btn-container">
                <button v-on:click="clearAllTask" class="clear-all-btn">Clear All Task</button>
            </div>
        </ul>
    </div>

</template>


<style scoped>
.todo-app {
    background-color: #fff;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 5px 3px rgba(0, 0, 0, 0.2);
    width: 100%;
    max-width: 600px;
    margin: 30px auto;
}

.todo-app h1 {
    text-align: center;
    margin-bottom: 20px;
    color: #00bf72;
}

.todo-app .task-input {
    background-color: #f2f2f2;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 20px;
    margin-bottom: 20px;
}

.todo-app .task-input input {
    background-color: #f2f2f2;
    padding: 10px;
    border: none;
    width: 100%;
    height: 60px;
    border-radius: 20px;
    outline: none;
}

.todo-app .task-input .add-task-btn {
    padding: 10px;
    border: none;
    background-color: #00bf72;
    color: #fff;
    font-weight: 700;
    width: 200px;
    height: 60px;
    border-radius: 20px;
    cursor: pointer;
}

.todo-app .task-list h2 {
    margin-bottom: 20px;
    color: #00bf72;
}

.todo-app .task-list .task-item {
    margin-bottom: 20px;
    display: flex;
    justify-content: space-between;
    border-bottom: 1px solid #f2f2f2;
    padding-bottom: 10px;
}

.todo-app .task-list .task-item:last-child {
    margin-bottom: unset;
}

.todo-app .task-list .action-btn {
    display: flex;
    align-items: center;
    column-gap: 10px;
}

.todo-app .task-list .remove-task {
    background-color: #bf0000;
    border: none;
    color: #fff;
    padding: 5px;
    border-radius: 5px;
    cursor: pointer;
}

.clear-all-btn-container {
    display: flex;
    justify-content: flex-end;
}

.clear-all-btn {
    background-color: #bf0000;
    border: none;
    color: #fff;
    padding: 5px;
    border-radius: 5px;
    cursor: pointer;
}
</style>