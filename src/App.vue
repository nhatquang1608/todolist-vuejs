<template>
  <div id="app">
    <div class="header">
      <h1>Todo List</h1>
    </div>
	<mark-todo
	@handleCheckAll="handleCheckAll"
	@handleDeleteAll="handleDeleteAll"/>
    <todo-list 
	:listTodo="listTodo" 
	@handleDeleteTodo="handleDeleteTodo"
	@handleMarkTodo="handleMarkTodo"
	@handleAddTodo="handleAddTodo"
	:isEditting="isEditting"
	@handleCancelEdit="handleCancelEdit"
	@handleOpenEditTodo="handleOpenEditTodo"
	:idEditting="idEditting"
	@handleEditTodo="handleEditTodo"/>
  </div>
</template>

<script>
import MarkTodo from './components/MarkTodo.vue';
import TodoList from './components/TodoList.vue';
import {v4 as uuidv4} from 'uuid';
export default {
  	name: 'app',
  	data () {
    	return {
			isEditting: false,
			idEditting: -1,
			allCompleted: false,
      		listTodo: [
				{
					id: uuidv4(),
					title: 'Wake up',
					completed: false
				},
			],
    	}
  	},
  	components: {
		MarkTodo,
    	TodoList,
  	},
  	methods: {
    	handleDeleteTodo(data) {
      		var indexDelete = -1
			this.listTodo.forEach((u, idx) => {
				if(u.id === data.id){
					indexDelete = idx
				}
			})
			if(indexDelete != -1){
				this.listTodo.splice(indexDelete,1)
			}
    	},
		handleMarkTodo(data) {
      		var indexMark = -1
			this.listTodo.forEach((u, idx) => {
				if(u.id === data.id){
					indexMark = idx
				}
			})
			if(indexMark != -1){
				this.listTodo[indexMark].completed = !this.listTodo[indexMark].completed
			}
    	},
		handleAddTodo(data) {
			this.listTodo.push(data)
		},
		handleCancelEdit() {
			this.isEditting = false
		},
		handleOpenEditTodo(data) {
			var indexEdit = -1
			this.listTodo.forEach((u, idx) => {
				if(u.id === data.id){
					indexEdit = idx
				}
			})
			if(indexEdit != -1){
				this.idEditting = indexEdit
			}
		},
		handleEditTodo(data) {
			this.listTodo[this.idEditting].title = data.title
		},
		handleCheckAll() {
			if(this.allCompleted === false) {
				this.listTodo.forEach((u) => {
					u.completed = true
				})
				this.allCompleted = true
			}
			else if(this.allCompleted === true) {
				this.listTodo.forEach((u) => {
					u.completed = false
				})
				this.allCompleted = false
			}
		},
		handleDeleteAll() {
			this.listTodo.splice(0,this.listTodo.length)
		}
  	}
}
</script>

<style>
* {
  box-sizing: border-box;
  font-family: Roboto, sans-serif;
}
.header {
  background-color: #333;
  height: 100px;
  color: rgb(255, 204, 0);
}
h1 {
  line-height: 100px;
  text-align: center;
  margin: 0;
}
#app {
	background-color: rgb(255, 242, 192);
	border-left: 1px solid #333;
	border-right: 1px solid #333;
}
</style>
