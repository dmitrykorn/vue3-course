<template>
	<div class="app">
		<form @submit.prevent>
			<h4>Создание поста</h4>
			<input v-model="post.title" class="input" type="text" placeholder="Название">
			<input v-model="post.body" class="input" type="text" placeholder="Описание">
			<button class="btn" @click="createPost">Создать</button>
		</form>
	</div>
</template>

<script>
import { createApp } from 'vue';

export default {
	data() {
		return {
			post: {
				title: '',
				body: ''
			}
		}
	},
	methods: {
		createPost() {
			this.post.id = Date.now();
			this.$emit('create', this.post, 'second param', '3 param')
			this.post = {
				title: '',
				body: ''
			}
		}
	}
}
</script>

<style scoped>
form {
	display: flex;
	flex-direction: column;
}

.input {
	width: 100%;
	border: 1px solid teal;
	padding: 10px 15px;
	margin-top: 15px;
}

.btn {
	margin-top: 15px;
	align-self: flex-end;
	padding: 10px 15px;
	background: none;
	color: teal;
	border: 1px solid teal;
}
</style>