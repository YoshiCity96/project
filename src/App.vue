<template>
<div class="app">
	<h1>Страница с постами</h1>
	<div class="app__btns">
<my-button
	@click="showDialog"
	>Создать пост</my-button>
	<my-select
	v-model="selectedSort"
	:options="sortOptions"
	></my-select>
	</div>
	
	<my-dialog v-model:show="dialogVisible" >
<post-form @create="CreatePost"/>
	</my-dialog>
	
	<post-list :posts="sortedPosts"
	@remove = "removePost"
	v-if="!isPostsLoading"
	/>
	<div v-else>Идёт загрузка...</div>

</div>
</template>

<script>
import PostForm from "./components/PostForm.vue";
import PostList from "./components/PostList.vue";
import MyButton from './components/UI/MyButton.vue';
import MyDialog from './components/UI/MyDialog.vue';
import axios from "axios";
import MySelect from './components/UI/MySelect.vue';


export default{
	components:{
		PostList,PostForm,MyDialog,
		MyButton,MySelect
	},
	data(){
		return{
			posts:[],
			dialogVisible:false,
			isPostsLoading:false,
			selectedSort: '',
			sortOptions: [
				{value: 'title', name: 'По названию'},
				{value: 'body', name: 'По описанию'}
			] 
	
	}
	},
	methods:{
		CreatePost(post){
			this.posts.push(post);
			this.dialogVisible=false;
		},
		removePost(post){
			this.posts = this.posts.filter(p => p.id !== post.id)
		},

		showDialog(){
			this.dialogVisible=true;
		},

		async fetchPosts(){
			try{
				this.isPostsLoading = true;
				
				const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10');
				this.posts=response.data;

			}
			catch(e){
				alert("error");
			} finally{
				this.isPostsLoading=false;
			}
		}
		
	
	},

	mounted(){
		this.fetchPosts();
	},
	computed:{
		sortedPosts(){
			return [...this.posts].sort((post1,post2) =>
			post1[this.selectedSort]?.localeCompare(post2[this.selectedSort])
			)
		}
	}
	
}
</script>

<style>
*{
	margin: 0;
	padding: 0;
	box-sizing: border-box;
	font-size: 22px;
}
.app{
	padding: 20px;
}

.app__btns{
	display: flex;
	justify-content: space-between;
	margin:20px 0;
}



</style>