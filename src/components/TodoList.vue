<template>
	<div>
		<p class="tasks">Completed Tasks: {{todos.filter(t => {return t.done === true}).length}}</p>
		<p class="tasks">Pending Tasks: {{todos.filter(t => {return t.done === false}).length}}</p>
		<todo @delete="deleteTodo" v-for="(todo, index) in todos" :todo="todo" :key="index"></todo>
	</div>
</template>


<script type = "text/javascript">
import Todo from './Todo';

export default {
	props: ['todos'],
	components: {
    	Todo
  	},
	methods: {
		deleteTodo(todo) {
			const todoIndex = this.todos.indexOf(todo);
			this.todos.splice(todoIndex, 1);
		}
	},
};
</script>

<style scoped>
p.tasks {
	text-align: center;
 }
</style>