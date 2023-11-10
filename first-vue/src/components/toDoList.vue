<script setup> 
import { ref } from "vue";
let id = 0;
const todos = ref([
    { id: 1, work: "Homework" },
    { id: 2, work: "cooking" },
    { id: 3, work: "Hello" },
    { id: 4, work: "Mink" },
    ]);


const newTodo = ref("");

const addTodo = () => {
    let todoObj = {
        id: id++,
        work: newTodo.value,
    };
    todos.value.push(todoObj);
};

const removeTodo = (todo) => {
    console.log(todo);
    todos.value = todos.value.filter((td) => td != todo);
};
</script>

<template>
    <h1>My TODO List</h1>
    <!-- <input type="text"> -->
    <input v-model="newTodo"/>
    <button @click="addTodo()">Add Todo</button>
    <ul>
        <li v-for="todo in todos" :key="todo.id">
            {{ todo.work }}
            <button @click="removeTodo(todo)" class="close">X</button>
        </li>
    </ul>
</template>