<script setup>
import { useTodoListStore } from "../stores/todoList"
import { storeToRefs } from "pinia"

const store = useTodoListStore()
// storeToRefs lets todoList keep reactivity:
const { todoList } = storeToRefs(store)

// destructuring action method doesn't require using storeToRefs:
//However, we need to make sure that we have brought toggleCompleted into the component
//.Since it’s an action method and not a reactive state property, we won’t use storeToRefs for toggleCompleted, DeleteTodo:
const { toggleCompleted, deleteTodo } = store

</script>

<template>
    <div v-for="todo in todoList" :key="todo.id" class="item">
        <div class="content">
            <span :class="{ completed: todo.completed }">{{ todo.item }}</span>
            <div>
                <span @click.stop="toggleCompleted(todo.id)">&#10004;</span>
                <span @click="deleteTodo(todo.id)" class="x">&#10060;</span>
            </div>
            

        </div>
    </div>
</template>

<style scoped>
span {
  margin: 0 10px;
  cursor: pointer;
}
.item {
  display: flex;
  justify-content: center;
}
.content {
  display: flex;
  font-size: 1.5em;
  justify-content: space-between;
  width: 80vw;
  padding: 5px;
}
.completed {
  text-decoration: line-through;
}
</style>