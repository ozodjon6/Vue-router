<script setup>
import axios from "axios";
import {onMounted, ref} from "vue";
import {useRoute} from 'vue-router';

const  route = useRoute();
const todo = ref('');

const id = route.params.id;

onMounted(() => {
	axios.get(`https://jsonplaceholder.typicode.com/todos/${id}`).then(res => todo.value = res.data);
})

</script>

<template>
	<h1>Products Details</h1>
	<pre>
		<strong>{{todo}}</strong>
	</pre>
</template>
