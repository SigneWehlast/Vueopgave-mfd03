<script setup>
import { ref } from 'vue';

    let tasks = ref(["Dishes", "Laundry", "Vacuum"]);
    let addTask = ref("");
    const isEditable = ref(true);

    const addTaskToList = () => {
        if (addTask.value.trim() !== "") {
        tasks.value.push(addTask.value);
        addTask.value = "";
    }
    };

    const deleteTask = (index) => {
    tasks.value.splice(index, 1);
    };
</script>

<template>
    <div class="to-do">
        <h1 class="to-do__title">ToDo list</h1>
        <ul>
            <li class="to-do__list" v-for="(item, index) in tasks" :key="index">
                <span :contenteditable="isEditable"> {{ item }} </span>
                <button class="to-do__button to-do__button-delete" @click="deleteTask(index)">Delete</button>
            </li>
            <li class="to-do__list" v-show="addTask">
                {{ addTask }}
            </li>
        </ul>

        <button class="to-do__button to-do__button-edit" @click="isEditable = !isEditable">
            {{ isEditable ? 'Save tasks' : 'Edit tasks' }}
        </button>

        <p class="to-do__text">Add a task to the list:</p>
        <input class="to-do__input-new-item" v-model="addTask" placeholder="New task" />
        <button class="to-do__button to-do__button-add" @click="addTaskToList" v-bind:disabled="!addTask">Add task</button>
    </div>
</template>

<style scoped lang="scss">
  @use "@/assets/scss/toDoList.scss";
</style>