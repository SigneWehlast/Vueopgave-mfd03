<script setup>
import { ref } from 'vue';

    let thingsToDo = ref(["Dishes", "Laundry", "Vacuum"]);
    let addItem = ref("");
    const isEditable = ref(true);

    const addToList = () => {
        if (addItem.value.trim() !== "") {
        thingsToDo.value.push(addItem.value);
        addItem.value = "";
    }
    };

    const deleteTask = (index) => {
    thingsToDo.value.splice(index, 1);
    };
</script>

<template>
    <div class="to-do">
        <h1 class="to-do__title">ToDo list</h1>
        <ul>
            <li class="to-do__list" v-for="(item, index) in thingsToDo" :key="index">
                <span :contenteditable="isEditable"> {{ item }} </span>
                <button class="to-do__button to-do__button-delete" @click="deleteTask(index)">Delete</button>
            </li>
            <li class="to-do__list" v-show="addItem">
                {{ addItem }}
            </li>
        </ul>

        <button class="to-do__button to-do__button-edit" @click="isEditable = !isEditable">
            {{ isEditable ? 'Save task' : 'Edit tasks' }}
        </button>

        <p class="to-do__text">Add items to the list:</p>
        <input class="to-do__input-new-item" v-model="addItem" placeholder="Type a new task" />
        <button class="to-do__button to-do__button-add" @click="addToList" v-bind:disabled="!addItem">Add item</button>
    </div>
</template>

<style scoped lang="scss">
.to-do {
  background: #CBC3E3;
  border-radius: 2em;
  display: flex;
  flex-direction: column;
  align-items: center; 
  justify-content: center;
  padding: 2em;
  width: 40%;
  margin: auto;

  &__title {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    margin-bottom: 0; 
  }

  &__list {
    font-family: sans-serif;
    color: black;
    margin-bottom: 0.5em;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  &__button {
    padding: 0.5em 1em;
    border: none;
    color: white;
    border-radius: 0.5em;
    margin-left: 1em;

    &-delete {
      background-color: #ff5252;
    }

    &-edit {
      background-color: #2196f3;
    }

    &-add {
      background-color: #4caf50;
      margin-top: 1em;
    }
  }

  &__input-new-item {
    padding: 0.5em;
    max-width: 50%;
    border-radius: 0.5em;
    border: 1px solid #ccc;
  }
}
</style>