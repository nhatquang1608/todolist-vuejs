<template>
    <div class="item">
        <div class="item-todo"
        :class="{completed:todo.completed}">
            <input type="checkbox" 
            :checked="todo.completed" 
            @change="markItemCompleted">
            <p>{{todo.title}}</p>
        </div>
        <div class="btn">
            <button class="btn-edit" @click="OpenEditTodo">...</button>
            <button class="btn-delete" @click="DeleteTodo">X</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'item',
    props: {
        todo: {
            type: Object,
            default: null
        },
    },
    data() {
        return {
        }
    },
    components: {
    },
    methods: {
        DeleteTodo() {
            var data = {
                id: this.todo.id
            }
            this.$emit('DeleteTodo', data)
        },
        markItemCompleted() {
            var data = {
                id: this.todo.id
            }
            this.$emit('MarkTodo', data)
        },
        OpenEditTodo() {
            var data = {
                id: this.todo.id
            }
            this.$emit('OpenEditTodo', data)
        }
    }
}
</script>

<style>
.item {
    display: flex;
    justify-content: space-between;
    border-bottom: 1px solid #333;
    padding: 0 15px;
}
.item-todo {
    display: flex;
}
.item-todo p {
    margin-left: 15px;
}
.completed {
    text-decoration: line-through;
}
.btn {
    height: 50px;
    padding-top: 10px;
}
.btn button {
    height: 30px;
    color: #fff;
    border: none;
    width: 30px;
}
.btn button:hover {
    cursor: pointer;
    opacity: 70%;
}
.btn-edit {
    background-color: rgb(0, 114, 207);
}
.btn-delete {
    background-color: red;
}
</style>