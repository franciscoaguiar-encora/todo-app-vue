<script setup>
import TodoForm from './TodoForm.vue'
import TodoList from './TodoList.vue';
</script>

<template>
    <div class="todo-app">
        <h1>To Do List</h1>
        <TodoForm></TodoForm>
        <TodoList></TodoList>
    </div>
</template>

<style scoped>
</style>