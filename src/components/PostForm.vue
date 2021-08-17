<template>
	<form @submit.prevent>
		<h4>Создание поста</h4>
		<input class="input" v-model="post.title" type="text" placeholder="Название">
		<input class="input" v-model="post.body" type="text" placeholder="Описание">
		<my-button style="align-self: flex-end; margin-top: 15px;" class="btn" @click="CreatePost" >Создать</my-button>
	</form>
</template>


<script>
import MyButton  from './UI/MyButton.vue';
export default {
	components:{
		MyButton
	},
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


</style>