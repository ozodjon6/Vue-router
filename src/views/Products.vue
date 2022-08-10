<script setup>
import axios from	'axios'
import {onMounted, ref} from "vue";
const todos = ref('');

onMounted(() => {
	axios.get('https://jsonplaceholder.typicode.com/todos/').then(res => todos.value = res.data )
})

</script>

<template>
	<h1>Products page</h1>
	<div class="wrapper">
		<router-link v-for="todo in todos" :key="todo.id" :to="{name: 'ProductsDetails', params: {id: todo.id}}">
			<h3>{{todo.id}}. {{todo.title}}</h3>
		</router-link>
	</div>
</template>

<style scoped>

.wrapper a h3 {
	color: #181818;
	transition: all 0.3s;
	display: block;
}
.wrapper a h3:hover {
	color: red;
	text-decoration: underline;
}

</style>
