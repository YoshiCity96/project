<template>
<div class="app">
	
	<post-form @create="CreatePost"/>
	<post-list :posts="posts" />


</div>
</template>

<script>
import PostForm from "./components/PostForm.vue";
import PostList from "./components/PostList.vue";
export default{
	components:{
		PostList,PostForm
	},
	data(){
		return{
			posts:[
				{id: 1, title:'Javascript 1',body:'opicanie js 1'},
				{id:2,title:'Javascript 2',body:'opicanie js 2'},
				{id:3,title:'Javascript 3',body:'opicanie js 3'},
			],
	
	}
	},
	methods:{
		CreatePost(post){
			this.posts.push(post);
		}
	
	}
}
</script>

<style>
*{
	margin: 0;
	padding: 0;
	box-sizing: border-box;
	font-size: 18px;
}
.app{
	padding: 20px;
}



</style>