<template>
	<form @submit.prevent>
		<h4>Создание поста</h4>
		<input class="input" v-model="post.title" type="text" placeholder="Название">
		<input class="input" v-model="post.body" type="text" placeholder="Описание">
		<button class="btn" @click="CreatePost" >Создать</button>
	</form>
</template>


<script>
export default {
data(){
	return{
		post:{
			title:'',
			body:''
		}
	}
},
methods:{
	CreatePost(){
			this.post.id = Date.now();
			this.$emit('create', this.post);
			this.post={
			title:'',
			body:''
			}
			
		}
}
}
</script>

<style  scoped>
form{
	display: flex;
	flex-direction: column;
}

.input{
	padding: 10px;
	width: 100%;
	margin-top: 10px;
}

.btn{
	align-self: flex-end;
	margin-top: 15px;
	background: none;
	border: 2px solid orange;
	padding: 10px;
	border-radius: 5px;
}
</style>