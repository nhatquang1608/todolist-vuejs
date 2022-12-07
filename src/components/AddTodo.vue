<template>
    <div class="add-todo">
        <input type="text" placeholder="Add new todo..." id="add">
        <button @click="addTodo">Add</button>
    </div>
</template>

<script>
import {v4 as uuidv4} from 'uuid';
export default {
    name: 'add-todo',
    data() {
        return {
            id: 0,
        }
    },
    methods: {
        addTodo() {
            var s = document.getElementById('add').value

            const newTodo = {
                id: uuidv4(),
                title: s,
                completed: false
            }

            this.$emit('AddTodo', newTodo)
        }
    }
}
</script>

<style>
.add-todo {
    padding: 15px;
    border-bottom: 1px solid #333;
    background-color: rgb(255, 204, 0);
    justify-content: space-between;
    display: flex;
}
.add-todo input {
    width: 1320px;
    padding-left: 15px;
}
.add-todo button {
    background-color: rgb(0, 187, 66);
    border: none;
    width: 80px;
    height: 30px;
    text-align: center;
    color: #fff;
}
.add-todo button:hover {
    cursor: pointer;
}
</style>