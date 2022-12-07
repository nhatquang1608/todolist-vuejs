<template>
    <div class="edit-todo"
    :class="getOpen">
        <div class="edit">
            <p>~ Edit todo ~</p>
            <div class="edit-content">
                <input type="text" placeholder="Edit todo..." id="edit">
                <button class="btn-save" @click="editTodo">Save</button>
                <button class="btn-cancel" @click="cancelEditTodo">Cancel</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'edit-todo',
    props: {
        isEditted: {
            type: Boolean,
            default: false
        },
    },
    data() {
        return {
        }
    },
    methods: {
        editTodo() {
            var s = document.getElementById('edit').value
            var data = {
                title: s
            }
            this.$emit('EditTodo', data)
            this.$emit('CancelEdit')
            this.$emit('MarkTodo', data)
        },
        cancelEditTodo() {
            this.$emit('CancelEdit')
        }
    },
    computed: {
        getOpen: function() {
            return {
                "open": this.isEditted
            }
        },
    }
}
</script>

<style>
.edit-todo {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.4);
    opacity: 0;
    visibility: hidden;
    transition: all .3s ease;
}
.edit-todo.open {
    opacity: 1;
    visibility: visible;
}
.edit {
    position: absolute;
    background-color: rgb(255, 204, 0);
    width: 500px;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) scale(1.2);
    padding: 30px;
    transition: all .3s ease;
}
.edit-content {
    justify-content: space-between;
    display: flex;
}
.edit p {
    text-align: center;
    margin: 0;
    padding-bottom: 30px;
    font-size: 25px;
    font-weight: 700;
}
.open .edit {
    transform: translate(-50%, -50%) scale(1);
}
.edit-todo input {
    width: 250px;
    padding-left: 15px;
}
.edit-todo button {
    border: none;
    width: 80px;
    height: 30px;
    text-align: center;
    color: #fff;
}
.btn-save {
    background-color: rgb(0, 114, 207);
}
.btn-cancel {
    background-color: red;
}
</style>