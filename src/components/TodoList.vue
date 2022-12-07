<template>
    <div class="todo-list">
        <add-todo @AddTodo="AddTodo"/>
        <todo-item 
        v-for="todo in listTodo" 
        :key="todo.id"
        :todo="todo"
        @DeleteTodo="DeleteTodo"
        @MarkTodo="MarkTodo"
        @OpenEditTodo="OpenEditTodo"/>
        <edit-todo 
        :isEditted="isEditted"
        @CancelEdit="CancelEdit"
        @EditTodo="EditTodo"/>
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue';
import AddTodo from './AddTodo.vue';
import EditTodo from './EditTodo.vue';
export default {
    name: 'todo-list',
    props: {
        listTodo: {
            type: Array,
            default: []
        },
        isEditting: {
            type: Boolean,
            default: false
        },
        idEditting: {
            type: Number,
            default: -1
        }
    },
    data() {
        return {
            isEditted: this.isEditting,
        }
    },
    components: {
        TodoItem,
        AddTodo,
        EditTodo,
    },
    methods: {
        DeleteTodo(data) {
            this.$emit('handleDeleteTodo', data)
        },
        MarkTodo(data) {
            this.$emit('handleMarkTodo', data)
        },
        AddTodo(data) {
            this.$emit('handleAddTodo', data)
        },
        OpenEditTodo(data) {
            this.isEditted = true
            this.$emit('handleOpenEditTodo', data)
        },
        CancelEdit() {
            this.isEditted = false
            this.$emit('handleCancelEdit')
        },
        EditTodo(data) {
            this.$emit('handleEditTodo', data)
        }
    }
}
</script>

<style>

</style>