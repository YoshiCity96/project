<template>
	<button class="btn">
		<slot></slot>
	</button>
</template>

<script>
export default{
 name:'my-button'
}

</script>

<style scoped>
.btn{
	
	
	background: none;
	border: 2px solid rgb(47, 175, 96);
	padding: 10px;
	border-radius: 5px;
}
</style>