<template>
	<div>
		<p class="tasks">Completed Tasks: {{todos.filter(t => {return t.done === true}).length}}</p>
		<p class="tasks">Pending Tasks: {{todos.filter(t => {return t.done === false}).length}}</p>
		<todo v-for="(todo, index) in todos" :todo="todo" :key="index"></todo>
	</div>
</template>


<script type = "text/javascript">
import Todo from './Todo';

export default {
	props: ['todos'],
	components: {
    	Todo
  	},
};
</script>

<style scoped>
p.tasks {
	text-align: center;
 }
</style>