<template>
    <div class="mark-todo">
        <div>
            <p>{{desc}}</p>
        </div>
        <div>
            <button class="btn-checkall" @click="checkAll">Check All</button>
            <button class="btn-deleteall" @click="deleteAll">Delete All</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'mark-todo',
    data () {
        return {
            desc: '@madebybom_ello<3tminnng',
        }
    },
    methods: {
        checkAll() {
            this.$emit('handleCheckAll')
        },
        deleteAll() {
            this.$emit('handleDeleteAll')
        }
    }
}
</script>

<style>
.mark-todo {
    background-color: rgb(255, 204, 0);
    padding: 15px;
    justify-content: space-between;
    display: flex;
}
.mark-todo button {
    border: none;
    width: 80px;
    height: 30px;
    text-align: center;
    color: #fff;
}
.mark-todo button:hover {
    cursor: pointer;
}
.btn-checkall {
    background-color: rgb(0, 187, 66);
}
.btn-deleteall {
    background-color: red;
}
.mark-todo p {
    color: #333;
    margin: 0;
}
</style>